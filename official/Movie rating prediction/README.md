# Movie rating prediction

<table>

<thead>

<tr>

<th>year</th>

<th>duration</th>

<th>nominations</th>

<th>categories</th>

<th>rating</th>

</tr>

</thead>

<tbody>

<tr>

<td>1921</td>

<td>3240</td>

<td>0</td>

<td>comedy drama</td>

<td>8.4</td>

</tr>

<tr>

<td>1925</td>

<td>5700</td>

<td>1</td>

<td>adventure comedy</td>

<td>8.3</td>

</tr>

<tr>

<td>1927</td>

<td>9180</td>

<td>4</td>

<td>drama comedy scifi</td>

<td>8.4</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
--data_csv movie_ratings.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">year</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">duration</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">nominations</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">categories</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">set</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">rating</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
```

</div>
