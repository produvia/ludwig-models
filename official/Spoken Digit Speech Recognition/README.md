# Spoken Digit Speech Recognition

This is a complete example of training an spoken digit speech recognition model on the "MNIST dataset of speech recognition".

### Download the free spoken digit dataset.[¶](#download-the-free-spoken-digit-dataset "Permanent link")

```
$ git clone https://github.com/Jakobovski/free-spoken-digit-dataset.git
mkdir speech_recog_digit_data
cp -r free-spoken-digit-dataset/recordings speech_recog_digit_data
cd speech_recog_digit_data
```

</div>

### Create an experiment CSV.[¶](#create-an-experiment-csv "Permanent link")

```
$ echo "audio_path","label" >> "spoken_digit.csv"
cd "recordings"
ls | while read -r file_name; do
   audio_path=$(readlink -m "${file_name}")
   label=$(echo ${file_name} | cut -c1)
   echo "${audio_path},${label}" >> "../spoken_digit.csv"
done
cd "../"
```

</div>

Now you should have `spoken_digit.csv` containing 2000 examples having the following format

<table>

<thead>

<tr>

<th>audio_path</th>

<th>label</th>

</tr>

</thead>

<tbody>

<tr>

<td>.../speech_recog_digit_data/recordings/0_jackson_0.wav</td>

<td>0</td>

</tr>

<tr>

<td>.../speech_recog_digit_data/recordings/0_jackson_10.wav</td>

<td>0</td>

</tr>

<tr>

<td>.../speech_recog_digit_data/recordings/0_jackson_11.wav</td>

<td>0</td>

</tr>

<tr>

<td>...</td>

<td>...</td>

</tr>

<tr>

<td>.../speech_recog_digit_data/recordings/1_jackson_0.wav</td>

<td>1</td>

</tr>

</tbody>

</table>

### Train a model.[¶](#train-a-model_1 "Permanent link")

From the directory where you have virtual environment with ludwig installed:

```
$ ludwig experiment \
  --data_csv <PATH_TO_SPOKEN_DIGIT_CSV> \
  --model_definition_file model_definition_file.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">audio_path</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">audio</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">stacked_cnn</span>
        <span class="nt">preprocessing</span><span class="p">:</span>
            <span class="nt">audio_feature</span><span class="p">:</span>
                <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">fbank</span>
                <span class="nt">window_length_in_s</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">0.025</span>
                <span class="nt">window_shift_in_s</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">0.01</span>
                <span class="nt">num_filter_bands</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">80</span>
            <span class="nt">audio_file_length_limit_in_s</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">1.0</span>
            <span class="nt">norm</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">per_file</span>
        <span class="nt">reduce_output</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">concat</span>
        <span class="nt">conv_layers</span><span class="p">:</span>
            <span class="p p-Indicator">-</span>
                <span class="nt">num_filters</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">16</span>
                <span class="nt">filter_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">6</span>
                <span class="nt">pool_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">4</span>
                <span class="nt">pool_stride</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">4</span>
                <span class="nt">dropout</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">true</span>
            <span class="p p-Indicator">-</span>
                <span class="nt">num_filters</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">32</span>
                <span class="nt">filter_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">3</span>
                <span class="nt">pool_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">2</span>
                <span class="nt">pool_stride</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">2</span>
                <span class="nt">dropout</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">true</span>
        <span class="nt">fc_layers</span><span class="p">:</span>
            <span class="p p-Indicator">-</span>
                <span class="nt">fc_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">64</span>
                <span class="nt">dropout</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">true</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">label</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>

<span class="nt">training</span><span class="p">:</span>
    <span class="nt">dropout_rate</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">0.4</span>
    <span class="nt">early_stop</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">10</span>
```

</div>
