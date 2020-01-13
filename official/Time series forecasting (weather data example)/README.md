# Time series forecasting (weather data example)

This example illustrates univariate timeseries forecasting using historical temperature data for Los Angeles.

Dowload and unpack historical hourly weather data available on Kaggle https://www.kaggle.com/selfishgene/historical-hourly-weather-data

Run the following python script to prepare the training dataset:

```
$ import pandas as pd
from ludwig.utils.data_utils import add_sequence_feature_column

df = pd.read_csv(
    '<PATH_TO_FILE>/temperature.csv',
    usecols=['Los Angeles']
).rename(
    columns={"Los Angeles": "temperature"}
).fillna(method='backfill').fillna(method='ffill')

# normalize
df.temperature = ((df.temperature-df.temperature.mean()) /
                  df.temperature.std())

train_size = int(0.6 * len(df))
vali_size = int(0.2 * len(df))

# train, validation, test split
df['split'] = 0
df.loc[
    (
        (df.index.values >= train_size) &
        (df.index.values < train_size + vali_size)
    ),
    ('split')
] = 1
df.loc[
    df.index.values >= train_size + vali_size,
    ('split')
] = 2

# prepare timeseries input feature colum
# (here we are using 20 preceeding values to predict the target)
add_sequence_feature_column(df, 'temperature', 20)
df.to_csv('<PATH_TO_FILE>/temperature_la.csv')
```

</div>

```
$ ludwig experiment \
--data_csv <PATH_TO_FILE>/temperature_la.csv \
  --model_definition_file model_definition.yaml
```

</div>

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">temperature_feature</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">timeseries</span>
        <span class="nt">encoder</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">rnn</span>
        <span class="nt">embedding_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">32</span>
        <span class="nt">state_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">32</span>

<span class="nt">output_features</span><span class="p">:</span>
    <span class="p p-Indicator">-</span>
        <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">temperature</span>
        <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
```

</div>
