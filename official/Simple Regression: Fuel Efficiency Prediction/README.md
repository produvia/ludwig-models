# Simple Regression: Fuel Efficiency Prediction

This example replicates the Keras example at https://www.tensorflow.org/tutorials/keras/basic_regression to predict the miles per gallon of a car given its characteristics in the [Auto MPG](https://archive.ics.uci.edu/ml/datasets/auto+mpg) dataset.

<table>

<thead>

<tr>

<th>MPG</th>

<th>Cylinders</th>

<th>Displacement</th>

<th>Horsepower</th>

<th>Weight</th>

<th>Acceleration</th>

<th>ModelYear</th>

<th>Origin</th>

</tr>

</thead>

<tbody>

<tr>

<td>18.0</td>

<td>8</td>

<td>307.0</td>

<td>130.0</td>

<td>3504.0</td>

<td>12.0</td>

<td>70</td>

<td>1</td>

</tr>

<tr>

<td>15.0</td>

<td>8</td>

<td>350.0</td>

<td>165.0</td>

<td>3693.0</td>

<td>11.5</td>

<td>70</td>

<td>1</td>

</tr>

<tr>

<td>18.0</td>

<td>8</td>

<td>318.0</td>

<td>150.0</td>

<td>3436.0</td>

<td>11.0</td>

<td>70</td>

<td>1</td>

</tr>

<tr>

<td>16.0</td>

<td>8</td>

<td>304.0</td>

<td>150.0</td>

<td>3433.0</td>

<td>12.0</td>

<td>70</td>

<td>1</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
--data_csv auto_mpg.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">training</span><span class="p">:</span>
    <span class="nt">batch_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">32</span>
    <span class="nt">epochs</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">1000</span>
    <span class="nt">early_stop</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">50</span>
    <span class="nt">learning_rate</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">0.001</span>
    <span class="nt">optimizer</span><span class="p">:</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">rmsprop</span>
<span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Cylinders</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Displacement</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Horsepower</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Weight</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Acceleration</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">ModelYear</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Origin</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">MPG</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
        <span class="nt">optimizer</span><span class="p">:</span>
            <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">mean_squared_error</span>
        <span class="nt">num_fc_layers</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">2</span>
        <span class="nt">fc_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">64</span>
```

</div>
