# Multi-Task Learning

This example is inspired by the classic paper [Natural Language Processing (Almost) from Scratch](https://arxiv.org/abs/1103.0398) by Collobert et al..

<table>

<thead>

<tr>

<th>sentence</th>

<th>chunks</th>

<th>part_of_speech</th>

<th>named_entities</th>

</tr>

</thead>

<tbody>

<tr>

<td>San Francisco is very foggy</td>

<td>B-NP I-NP B-VP B-ADJP I-ADJP</td>

<td>NNP NNP VBZ RB JJ</td>

<td>B-Loc I-Loc O O O</td>

</tr>

<tr>

<td>My dog likes eating sausage</td>

<td>B-NP I-NP B-VP B-VP B-NP</td>

<td>PRP NN VBZ VBG NN</td>

<td>O O O O O</td>

</tr>

<tr>

<td>Brutus Killed Julius Caesar</td>

<td>B-NP B-VP B-NP I-NP</td>

<td>NNP VBD NNP NNP</td>

<td>B-Per O B-Per I-Per</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
--data_csv nl_data.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sentence</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sequence</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">rnn</span>
        <span class="nt">cell</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">lstm</span>
        <span class="nt">bidirectional</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">true</span>
        <span class="nt">reduce_output</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">null</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">chunks</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sequence</span>
        <span class="nt">decoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">tagger</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">part_of_speech</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sequence</span>
        <span class="nt">decoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">tagger</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">named_entities</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">sequence</span>
        <span class="nt">decoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">tagger</span>
```

</div>
