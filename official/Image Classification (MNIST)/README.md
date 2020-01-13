# Image Classification (MNIST)

This is a complete example of training an image classification model on the MNIST dataset.

### Download the MNIST dataset.[¶](#download-the-mnist-dataset "Permanent link")

```shell
$ git clone https://github.com/myleott/mnist_png.git
cd mnist_png/
tar -xf mnist_png.tar.gz
cd mnist_png/
```

</div>

### Create train and test CSVs.[¶](#create-train-and-test-csvs "Permanent link")

Open python shell in the same directory and run this:

```shell
$ import os
for name in ['training', 'testing']:
    with open('mnist_dataset_{}.csv'.format(name), 'w') as output_file:
        print('=== creating {} dataset ==='.format(name))
        output_file.write('image_path,label\n')
        for i in range(10):
            path = '{}/{}'.format(name, i)
            for file in os.listdir(path):
                if file.endswith(".png"):
                    output_file.write('{},{}\n'.format(os.path.join(path, file), str(i)))
```

</div>

Now you should have `mnist_dataset_training.csv` and `mnist_dataset_testing.csv` containing 60000 and 10000 examples correspondingly and having the following format

<table>

<thead>

<tr>

<th>image_path</th>

<th>label</th>

</tr>

</thead>

<tbody>

<tr>

<td>training/0/16585.png</td>

<td>0</td>

</tr>

<tr>

<td>training/0/24537.png</td>

<td>0</td>

</tr>

<tr>

<td>training/0/25629.png</td>

<td>0</td>

</tr>

</tbody>

</table>

### Train a model.[¶](#train-a-model "Permanent link")

From the directory where you have virtual environment with ludwig installed:

```shell
$ ludwig train \
  --data_train_csv <PATH_TO_MNIST_DATASET_TRAINING_CSV> \
  --data_test_csv <PATH_TO_MNIST_DATASET_TEST_CSV> \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">image_path</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">image</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">stacked_cnn</span>
        <span class="nt">conv_layers</span><span class="p">:</span>
            <span class="p p-Indicator">-</span>
                <span class="nt">num_filters</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">32</span>
                <span class="nt">filter_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">3</span>
                <span class="nt">pool_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">2</span>
                <span class="nt">pool_stride</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">2</span>
            <span class="p p-Indicator">-</span>
                <span class="nt">num_filters</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">64</span>
                <span class="nt">filter_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">3</span>
                <span class="nt">pool_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">2</span>
                <span class="nt">pool_stride</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">2</span>
                <span class="nt">dropout</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">true</span>
        <span class="nt">fc_layers</span><span class="p">:</span>
            <span class="p p-Indicator">-</span>
                <span class="nt">fc_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">128</span>
                <span class="nt">dropout</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">true</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">label</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>

<span class="nt">training</span><span class="p">:</span>
    <span class="nt">dropout_rate</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">0.4</span>
```

</div>