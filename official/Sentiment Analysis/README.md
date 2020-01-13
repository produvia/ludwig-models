# Sentiment Analysis

<table>

<thead>

<tr>

<th>review</th>

<th>sentiment</th>

</tr>

</thead>

<tbody>

<tr>

<td>The movie was fantastic!</td>

<td>positive</td>

</tr>

<tr>

<td>Great acting and cinematography</td>

<td>positive</td>

</tr>

<tr>

<td>The acting was terrible!</td>

<td>negative</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
  --data_csv sentiment.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">review</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">text</span>
        <span class="nt">level</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">word</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">parallel_cnn</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sentiment</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
```

</div>
