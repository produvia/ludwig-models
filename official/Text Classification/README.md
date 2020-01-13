# Text Classification

Text classification is the task of assigning a sentence or document an appropriate category. The categories depend on the chosen dataset and can range from topics. 

To learn more about text classification, visit [Ludwig](https://uber.github.io/ludwig/examples/#text-classification) or [Papers With Code](Papers With Code). 

## Reuters-21578

### Dataset

#### reuters-allcats.csv

| class | text |
| - | - |
|Neg- | 2 BAHIA COCOA REVIEW SALVADOR Feb 26 - Sh... |
|Neg- | 2 USX ltX DEBT DOWGRADED BY MOODYS NEW YOR... |
|Pos-earn | 2 COBANCO INC ltCBCO YEAR NET SANTA CRUZ ... |

### Model

```yaml
# model_definition.yaml

input_features:
    -
        name: text
        type: text
        level: word
        encoder: parallel_cnn

output_features:
    -
        name: class
        type: category
```

### Train

```shell
$ ludwig train \
  --data_csv reuters-allcats.csv \
  --model_definition_file model_definition.yaml
```

### Predict

```shell
$ ludwig predict \
  --data_csv reuters-allcats.csv \
  --model_path results/experiment_run/model/
```

### Experiment (Train and Predict)

```shell
$ ludwig experiment \
  --data_csv reuters-allcats.csv \
  --model_definition_file model_definition.yaml
```

## OHSUMED

### Dataset

#### ohsumed-allcats.csv

| class | text |
| --- | --- |
| Neg- | Laparoscopic treatment of perforated peptic ul... |
| Neg- | Experimental sympathetic activation causes end... |
| Pos-Hyperplasia | Myocyte cell loss and myocyte cellular hyperpl... |

### Model

```yaml
# model_definition.yaml

input_features:
    -
        name: text
        type: text
        level: word
        encoder: parallel_cnn

output_features:
    -
        name: class
        type: category
```

### Train

```shell
$ ludwig train \
  --data_csv text_classification.csv \
  --model_definition_file model_definition.yaml
```

### Predict

```shell
$ ludwig predict \
  --data_csv text_classification.csv \
  --model_path results/experiment_run/model/
```

### Experiment (Train and Predict)

```shell
$ ludwig experiment \
  --data_csv text_classification.csv \
  --model_definition_file model_definition.yaml
```

## Epinions.com

### Dataset

#### epinions-1.csv

| class  | text |
| - | - |
| Auto | I have recently purchased a J30T with moderat... |
| Camera | This camera is perfect for anyone who wants t... |
| Auto | 2000 Hyundai Elantra Wagon if you can find ... |

#### epinions-2.csv

| class  | text |
| - | - |
| OtherAuto | I had pen in hand ready to sign on the line ... |
| OtherAuto | The Mercedes Benz E 320 is the best car in th... |
| OtherAuto | After owning a toyota 4runner for 10 years no... |

### Model

```yaml
# model_definition.yaml

input_features:
    -
        name: text
        type: text
        level: word
        encoder: parallel_cnn

output_features:
    -
        name: class
        type: category
```

### Train

```shell
$ ludwig train \
  --data_csv epinions-1.csv \
  --model_definition_file model_definition.yaml
```

### Predict

```shell
$ ludwig predict \
  --data_csv epinions-1.csv \
  --model_path results/experiment_run/model/
```

### Experiment (Train and Predict)

```shell
$ ludwig experiment \
  --data_csv epinions-1.csv \
  --model_definition_file model_definition.yaml
```