# Natural Language Understanding

<table>

<thead>

<tr>

<th>utterance</th>

<th>intent</th>

<th>slots</th>

</tr>

</thead>

<tbody>

<tr>

<td>I want a pizza</td>

<td>order_food</td>

<td>O O O B-Food_type</td>

</tr>

<tr>

<td>Book a flight to Boston</td>

<td>book_flight</td>

<td>O O O O B-City</td>

</tr>

<tr>

<td>Book a flight at 7pm to London</td>

<td>book_flight</td>

<td>O O O O B-Departure_time O B-City</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
  --data_csv nlu.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">utterance</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">text</span>
        <span class="nt">level</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">word</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">rnn</span>
        <span class="nt">cell_type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">lstm</span>
        <span class="nt">bidirectional</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">true</span>
        <span class="nt">num_layers</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">2</span>
        <span class="nt">reduce_output</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">null</span>
        <span class="nt">preprocessing</span><span class="p">:</span>
          <span class="nt">word_format</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">space</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">intent</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
        <span class="nt">reduce_input</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sum</span>
        <span class="nt">num_fc_layers</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">1</span>
        <span class="nt">fc_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">64</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">slots</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sequence</span>
        <span class="nt">decoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">tagger</span>
```

</div>
