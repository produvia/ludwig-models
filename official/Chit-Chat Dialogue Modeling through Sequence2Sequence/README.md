# Chit-Chat Dialogue Modeling through Sequence2Sequence

<table>

<thead>

<tr>

<th>user1</th>

<th>user2</th>

</tr>

</thead>

<tbody>

<tr>

<td>Hello! How are you doing?</td>

<td>Doing well, thanks!</td>

</tr>

<tr>

<td>I got promoted today</td>

<td>Congratulations!</td>

</tr>

<tr>

<td>Not doing well today</td>

<td>I’m sorry, can I do something to help you?</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
  --data_csv chitchat.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">user1</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">text</span>
        <span class="nt">level</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">word</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">rnn</span>
        <span class="nt">cell_type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">lstm</span>
        <span class="nt">reduce_output</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">null</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">user2</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">text</span>
        <span class="nt">level</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">word</span>
        <span class="nt">decoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">generator</span>
        <span class="nt">cell_type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">lstm</span>
        <span class="nt">attention</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">bahdanau</span>
        <span class="nt">loss</span><span class="p">:</span>
            <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sampled_softmax_cross_entropy</span>

<span class="nt">training</span><span class="p">:</span>
    <span class="nt">batch_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">96</span>
```

</div>
