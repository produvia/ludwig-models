# Image Classification

<table>

<thead>

<tr>

<th>image_path</th>

<th>class</th>

</tr>

</thead>

<tbody>

<tr>

<td>images/image_000001.jpg</td>

<td>car</td>

</tr>

<tr>

<td>images/image_000002.jpg</td>

<td>dog</td>

</tr>

<tr>

<td>images/image_000003.jpg</td>

<td>boat</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
  --data_csv image_classification.csv \
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
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">class</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
```
