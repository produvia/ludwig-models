# Multi-label classification

<table>

<thead>

<tr>

<th>image_path</th>

<th>tags</th>

</tr>

</thead>

<tbody>

<tr>

<td>images/image_000001.jpg</td>

<td>car man</td>

</tr>

<tr>

<td>images/image_000002.jpg</td>

<td>happy dog tie</td>

</tr>

<tr>

<td>images/image_000003.jpg</td>

<td>boat water</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
--data_csv image_data.csv \
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
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">tags</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">set</span>
```

</div>
