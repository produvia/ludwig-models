# Time series forecasting

While direct timeseries prediction is a work in progress Ludwig can ingest timeseries input feature data and make numerical predictions. Below is an example of a model trained to forecast timeseries at five different horizons.

<table>

<thead>

<tr>

<th>timeseries_data</th>

<th>y1</th>

<th>y2</th>

<th>y3</th>

<th>y4</th>

<th>y5</th>

</tr>

</thead>

<tbody>

<tr>

<td>15.07 14.89 14.45 ...</td>

<td>16.92</td>

<td>16.67</td>

<td>16.48</td>

<td>17.00</td>

<td>17.02</td>

</tr>

<tr>

<td>14.89 14.45 14.30 ...</td>

<td>16.67</td>

<td>16.48</td>

<td>17.00</td>

<td>17.02</td>

<td>16.48</td>

</tr>

<tr>

<td>14.45 14.3 14.94 ...</td>

<td>16.48</td>

<td>17.00</td>

<td>17.02</td>

<td>16.48</td>

<td>15.82</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
--data_csv timeseries_data.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">timeseries_data</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">timeseries</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">y1</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">y2</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">y3</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">y4</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">y5</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
```

</div>
