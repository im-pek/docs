page_type: reference
<style>{% include "site-assets/css/style.css" %}</style>

<!-- DO NOT EDIT! Automatically generated file. -->

# tf.keras.layers.Add

## Class `Add`

Layer that adds a list of inputs.



### Aliases:

* Class `tf.compat.v1.keras.layers.Add`
* Class `tf.compat.v2.keras.layers.Add`
* Class `tf.keras.layers.Add`



Defined in [`python/keras/layers/merge.py`](https://github.com/tensorflow/tensorflow/tree/r1.14/tensorflow/python/keras/layers/merge.py).

<!-- Placeholder for "Used in" -->

It takes as input a list of tensors,
all of the same shape, and returns
a single tensor (also of the same shape).

#### Examples:



```python
    import keras

    input1 = keras.layers.Input(shape=(16,))
    x1 = keras.layers.Dense(8, activation='relu')(input1)
    input2 = keras.layers.Input(shape=(32,))
    x2 = keras.layers.Dense(8, activation='relu')(input2)
    # equivalent to `added = keras.layers.add([x1, x2])`
    added = keras.layers.Add()([x1, x2])
    out = keras.layers.Dense(4)(added)
    model = keras.models.Model(inputs=[input1, input2], outputs=out)
```

<h2 id="__init__"><code>__init__</code></h2>

``` python
__init__(**kwargs)
```





