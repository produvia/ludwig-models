# One-shot Learning with Siamese Networks

This example can be considered a simple baseline for one-shot learning on the [Omniglot](https://github.com/brendenlake/omniglot) dataset. The task is, given two images of two handwritten characters, recognize if they are two instances of the same character or not.

<table>

<thead>

<tr>

<th>image_path_1</th>

<th>image_path_2</th>

<th>similarity</th>

</tr>

</thead>

<tbody>

<tr>

<td>balinese/character01/0108_13.png</td>

<td>balinese/character01/0108_18.png</td>

<td>1</td>

</tr>

<tr>

<td>balinese/character01/0108_13.png</td>

<td>balinese/character08/0115_12.png</td>

<td>0</td>

</tr>

<tr>

<td>balinese/character01/0108_04.png</td>

<td>balinese/character01/0108_08.png</td>

<td>1</td>

</tr>

<tr>

<td>balinese/character01/0108_11.png</td>

<td>balinese/character05/0112_02.png</td>

<td>0</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
--data_csv balinese_characters.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">image_path_1</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">image</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">stacked_cnn</span>
        <span class="nt">preprocessing</span><span class="p">:</span>
          <span class="nt">width</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">28</span>
          <span class="nt">height</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">28</span>
          <span class="nt">resize_image</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">true</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">image_path_2</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">image</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">stacked_cnn</span>
        <span class="nt">resize_image</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">true</span>
        <span class="nt">width</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">28</span>
        <span class="nt">height</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">28</span>
        <span class="nt">tied_weights</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">image_path_1</span>

<span class="nt">combiner</span><span class="p">:</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">concat</span>
    <span class="nt">num_fc_layers</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">2</span>
    <span class="nt">fc_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">256</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">similarity</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">binary</span>
```

</div>
