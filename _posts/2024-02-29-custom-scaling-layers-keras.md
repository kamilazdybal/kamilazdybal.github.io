---
layout: default
title:  "Learn the scale: Custom data scaling layers in Keras"
date:   2024-02-29 10:00:00 +0100
categories: jekyll update
---

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Learn the scale: Custom data scaling layers in Keras

Here's an example of how to construct the following neural architecture in Keras:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/centering-scaling-layer.png" width="700">
</p>

```python
import tensorflow as tf
from keras.models import Model
from keras.layers import Input, Dense
```

We set some initial parameters and random seeds for reproducibility:

```python
n_variables = 10
random_seed = 100
```

```python
tf.random.set_seed(random_seed)
tf.keras.utils.set_random_seed(random_seed)
kernel_initializer = tf.keras.initializers.GlorotUniform(seed=random_seed)
```

## Custom scaling layer

```python
class ScalingLayer(tf.keras.layers.Layer):

    def __init__(self):
        super().__init__()

    def build(self, input_shape):
        self.scaling_factors = self.add_weight(shape=(int(input_shape[-1]),), initializer=kernel_initializer)

    def call(self, inputs):
        return tf.multiply(inputs, self.scaling_factors)
```

Stack layers:

```python
input_layer = Input(shape=(n_variables,))
scaling_layer = ScalingLayer()(input_layer)
layer_2 = Dense(n_variables, activation='tanh', kernel_initializer=kernel_initializer)(scaling_layer)
layer_3 = Dense(n_variables, activation='tanh', kernel_initializer=kernel_initializer)(layer_2)
output_layer = Dense(n_variables, activation='tanh', kernel_initializer=kernel_initializer)(layer_3)
model = Model(input_layer, output_layer)
```

With model summary we'll be able to see all trainable parameters:

```python
model.summary()
```

```text
Model: "model"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 input_1 (InputLayer)        [(None, 10)]              0         

 scaling_layer (ScalingLaye  (None, 10)                10        
 r)                                                              

 dense (Dense)               (None, 10)                110       

 dense_1 (Dense)             (None, 10)                110       

 dense_2 (Dense)             (None, 10)                110       

=================================================================
Total params: 340 (1.33 KB)
Trainable params: 340 (1.33 KB)
Non-trainable params: 0 (0.00 Byte)
_________________________________________________________________
```

## Custom centering-scaling layer

```python
class CenteringScalingLayer(tf.keras.layers.Layer):

    def __init__(self):
        super().__init__()

    def build(self, input_shape):
        self.scaling_factors = self.add_weight(shape=(int(input_shape[-1]),), initializer=kernel_initializer)
        self.centering_factors = self.add_weight(shape=(int(input_shape[-1]),), initializer='zeros')

    def call(self, inputs):
        return tf.multiply(inputs, self.scaling_factors) + self.centering_factors
```

Stack layers:

```python
input_layer = Input(shape=(n_variables,))
scaling_layer = CenteringScalingLayer()(input_layer)
layer_2 = Dense(n_variables, activation='tanh', kernel_initializer=kernel_initializer)(scaling_layer)
layer_3 = Dense(n_variables, activation='tanh', kernel_initializer=kernel_initializer)(layer_2)
output_layer = Dense(n_variables, activation='tanh', kernel_initializer=kernel_initializer)(layer_3)
model = Model(input_layer, output_layer)
```

With model summary we'll be able to see all trainable parameters:

```python
model.summary()
```

```text
Model: "model_1"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 input_2 (InputLayer)        [(None, 10)]              0         

 centering_scaling_layer (C  (None, 10)                20        
 enteringScalingLayer)                                           

 dense_3 (Dense)             (None, 10)                110       

 dense_4 (Dense)             (None, 10)                110       

 dense_5 (Dense)             (None, 10)                110       

=================================================================
Total params: 350 (1.37 KB)
Trainable params: 350 (1.37 KB)
Non-trainable params: 0 (0.00 Byte)
_________________________________________________________________
```

We get 10 more trainable parameters in the centering_scaling_layer.
