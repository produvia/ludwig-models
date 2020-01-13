# Visual Question Answering

<table>

<thead>

<tr>

<th>image_path</th>

<th>question</th>

<th>answer</th>

</tr>

</thead>

<tbody>

<tr>

<td>imdata/image_000001.jpg</td>

<td>Is there snow on the mountains?</td>

<td>yes</td>

</tr>

<tr>

<td>imdata/image_000002.jpg</td>

<td>What color are the wheels</td>

<td>blue</td>

</tr>

<tr>

<td>imdata/image_000003.jpg</td>

<td>What kind of utensil is in the glass bowl</td>

<td>knife</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
--data_csv vqa.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">image_path</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">image</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">stacked_cnn</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">question</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">text</span>
        <span class="nt">level</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">word</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">parallel_cnn</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">answer</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">text</span>
        <span class="nt">level</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">word</span>
        <span class="nt">decoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">generator</span>
        <span class="nt">cell_type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">lstm</span>
        <span class="nt">loss</span><span class="p">:</span>
            <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sampled_softmax_cross_entropy</span>
```

</div>
