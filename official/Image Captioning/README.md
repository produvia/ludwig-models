# Image Captioning

<table>

<thead>

<tr>

<th>image_path</th>

<th>caption</th>

</tr>

</thead>

<tbody>

<tr>

<td>imagenet/image_000001.jpg</td>

<td>car driving on the street</td>

</tr>

<tr>

<td>imagenet/image_000002.jpg</td>

<td>dog barking at a cat</td>

</tr>

<tr>

<td>imagenet/image_000003.jpg</td>

<td>boat sailing in the ocean</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
--data_csv image captioning.csv \
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

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">caption</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">text</span>
        <span class="nt">level</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">word</span>
        <span class="nt">decoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">generator</span>
        <span class="nt">cell_type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">lstm</span>
```

</div>
