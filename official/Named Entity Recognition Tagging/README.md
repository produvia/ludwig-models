# Named Entity Recognition Tagging

<table>

<thead>

<tr>

<th>utterance</th>

<th>tag</th>

</tr>

</thead>

<tbody>

<tr>

<td>Blade Runner is a 1982 neo-noir science fiction film directed by Ridley Scott</td>

<td>Movie Movie O O Date O O O O O O Person Person</td>

</tr>

<tr>

<td>Harrison Ford and Rutger Hauer starred in it</td>

<td>Person Person O Person person O O O</td>

</tr>

<tr>

<td>Philip Dick 's novel Do Androids Dream of Electric Sheep ? was published in 1968</td>

<td>Person Person O O Book Book Book Book Book Book Book O O O Date</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
  --data_csv sequence_tags.csv \
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
        <span class="nt">reduce_output</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">null</span>
        <span class="nt">preprocessing</span><span class="p">:</span>
          <span class="nt">word_format</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">space</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">tag</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sequence</span>
        <span class="nt">decoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">tagger</span>
```

</div>
