# Speaker Verification

This example describes how to use Ludwig for a simple speaker verification task. We assume to have the following data with label 0 corresponding to an audio file of an unauthorized voice and label 1 corresponding to an audio file of an authorized voice. The sample data looks as follows:

<table>

<thead>

<tr>

<th>audio_path</th>

<th>label</th>

</tr>

</thead>

<tbody>

<tr>

<td>audiodata/audio_000001.wav</td>

<td>0</td>

</tr>

<tr>

<td>audiodata/audio_000002.wav</td>

<td>0</td>

</tr>

<tr>

<td>audiodata/audio_000003.wav</td>

<td>1</td>

</tr>

<tr>

<td>audiodata/audio_000004.wav</td>

<td>1</td>

</tr>

</tbody>

</table>

```
$ ludwig experiment \
--data_csv speaker_verification.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">audio_path</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">audio</span>
        <span class="nt">preprocessing</span><span class="p">:</span>
            <span class="nt">audio_file_length_limit_in_s</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">7.0</span>
            <span class="nt">audio_feature</span><span class="p">:</span>
                <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">stft</span>
                <span class="nt">window_length_in_s</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">0.04</span>
                <span class="nt">window_shift_in_s</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">0.02</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">cnnrnn</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">label</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">binary</span>
```

</div>
