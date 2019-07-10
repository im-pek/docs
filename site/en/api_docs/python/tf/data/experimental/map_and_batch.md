page_type: reference
<style>{% include "site-assets/css/style.css" %}</style>

<!-- DO NOT EDIT! Automatically generated file. -->

# tf.data.experimental.map_and_batch

Fused implementation of `map` and `batch`. (deprecated)

### Aliases:

* `tf.compat.v1.data.experimental.map_and_batch`
* `tf.compat.v2.data.experimental.map_and_batch`
* `tf.data.experimental.map_and_batch`

``` python
tf.data.experimental.map_and_batch(
    map_func,
    batch_size,
    num_parallel_batches=None,
    drop_remainder=False,
    num_parallel_calls=None
)
```



Defined in [`python/data/experimental/ops/batching.py`](https://github.com/tensorflow/tensorflow/tree/r1.14/tensorflow/python/data/experimental/ops/batching.py).

<!-- Placeholder for "Used in" -->

Warning: THIS FUNCTION IS DEPRECATED. It will be removed in a future version.
Instructions for updating:
Use <a href="../../../tf/data/Dataset#map"><code>tf.data.Dataset.map(map_func, num_parallel_calls)</code></a> followed by <a href="../../../tf/data/Dataset#batch"><code>tf.data.Dataset.batch(batch_size, drop_remainder)</code></a>. Static tf.data optimizations will take care of using the fused implementation.

Maps `map_func` across `batch_size` consecutive elements of this dataset
and then combines them into a batch. Functionally, it is equivalent to `map`
followed by `batch`. However, by fusing the two transformations together, the
implementation can be more efficient. Surfacing this transformation in the API
is temporary. Once automatic input pipeline optimization is implemented,
the fusing of `map` and `batch` will happen automatically and this API will be
deprecated.

#### Args:


* <b>`map_func`</b>: A function mapping a nested structure of tensors to another
  nested structure of tensors.
* <b>`batch_size`</b>: A <a href="../../../tf#int64"><code>tf.int64</code></a> scalar <a href="../../../tf/Tensor"><code>tf.Tensor</code></a>, representing the number of
  consecutive elements of this dataset to combine in a single batch.
* <b>`num_parallel_batches`</b>: (Optional.) A <a href="../../../tf#int64"><code>tf.int64</code></a> scalar <a href="../../../tf/Tensor"><code>tf.Tensor</code></a>,
  representing the number of batches to create in parallel. On one hand,
  higher values can help mitigate the effect of stragglers. On the other
  hand, higher values can increase contention if CPU is scarce.
* <b>`drop_remainder`</b>: (Optional.) A <a href="../../../tf#bool"><code>tf.bool</code></a> scalar <a href="../../../tf/Tensor"><code>tf.Tensor</code></a>, representing
  whether the last batch should be dropped in case its size is smaller than
  desired; the default behavior is not to drop the smaller batch.
* <b>`num_parallel_calls`</b>: (Optional.) A <a href="../../../tf#int32"><code>tf.int32</code></a> scalar <a href="../../../tf/Tensor"><code>tf.Tensor</code></a>,
  representing the number of elements to process in parallel. If not
  specified, `batch_size * num_parallel_batches` elements will be processed
  in parallel. If the value <a href="../../../tf/data/experimental#AUTOTUNE"><code>tf.data.experimental.AUTOTUNE</code></a> is used, then
  the number of parallel calls is set dynamically based on available CPU.


#### Returns:

A `Dataset` transformation function, which can be passed to
<a href="../../../tf/data/Dataset#apply"><code>tf.data.Dataset.apply</code></a>.



#### Raises:


* <b>`ValueError`</b>: If both `num_parallel_batches` and `num_parallel_calls` are
  specified.