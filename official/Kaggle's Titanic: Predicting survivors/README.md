# Kaggle's Titanic: Predicting survivors

This example describes how to use Ludwig to train a model for the [kaggle competition](https://www.kaggle.com/c/titanic/), on predicting a passenger's probability of surviving the Titanic disaster. Here's a sample of the data:

<table>

<thead>

<tr>

<th>Pclass</th>

<th>Sex</th>

<th>Age</th>

<th>SibSp</th>

<th>Parch</th>

<th>Fare</th>

<th>Survived</th>

<th>Embarked</th>

</tr>

</thead>

<tbody>

<tr>

<td>3</td>

<td>male</td>

<td>22</td>

<td>1</td>

<td>0</td>

<td>7.2500</td>

<td>0</td>

<td>S</td>

</tr>

<tr>

<td>1</td>

<td>female</td>

<td>38</td>

<td>1</td>

<td>0</td>

<td>71.2833</td>

<td>1</td>

<td>C</td>

</tr>

<tr>

<td>3</td>

<td>female</td>

<td>26</td>

<td>0</td>

<td>0</td>

<td>7.9250</td>

<td>0</td>

<td>S</td>

</tr>

<tr>

<td>3</td>

<td>male</td>

<td>35</td>

<td>0</td>

<td>0</td>

<td>8.0500</td>

<td>0</td>

<td>S</td>

</tr>

</tbody>

</table>

The full data and the column descriptions can be found [here](https://www.kaggle.com/c/titanic/data).

After downloading the data, to train a model on this dataset using Ludwig,

```
$ ludwig experiment \
  --data_csv <PATH_TO_TITANIC_CSV> \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Pclass</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Sex</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Age</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
        <span class="nt">preprocessing</span><span class="p">:</span>
          <span class="nt">missing_value_strategy</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">fill_with_mean</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">SibSp</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Parch</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Fare</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
        <span class="nt">preprocessing</span><span class="p">:</span>
          <span class="nt">missing_value_strategy</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">fill_with_mean</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Embarked</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">Survived</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">binary</span>
```

</div>

Better results can be obtained with morerefined feature transformations and preprocessing, but this example has the only aim to show how this type do tasks and data can be used in Ludwig.
