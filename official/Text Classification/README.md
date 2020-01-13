# Text Classification

Text classification is the task of assigning a sentence or document an appropriate category. The categories depend on the chosen dataset and can range from topics. 

To learn more about text classification, visit [Ludwig](https://uber.github.io/ludwig/examples/#text-classification) or [Papers With Code](https://paperswithcode.com/task/text-classification). 

## Reuters-21578

### Dataset

Reuters-21578 is a well-known newswire dataset. It contains 21,578 newswire documents, so it is now considered too small for serious research and development purposes. However, the text and categories are similar to text and categories used in industry.

There are many Reuters categories. In this assignment you will consider 6 categories. Two are 'big' categories (many positive documents), two are 'medium' categories, and two are 'small' categories (few positive documents).

- Small categories: heat, housing
- Medium categories: coffee, gold
- Big categories: acq, earn

reuters-allcats.csv covers all 6 classes

To learn more about Reuters-21578 dataset, visit [Carnegie Mellon University](http://boston.lti.cs.cmu.edu/classes/95-865-K/HW/HW2/).

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

OHSUMED is a well-known medical abstracts dataset. It contains 348,566 references, and is still used for research and development.

There are many OHSUMED categories. In this assignment you will consider 6 categories. Two are 'big' categories (many positive documents), two are 'medium' categories, and two are 'small' categories (few positive documents).

- Small categories: Mitosis, Pediatrics
- Medium categories: Necrosis, Hyperplasia
- Big categories: Pregnancy, Rats

ohsumed-allcats.csv covers all 6 classes.

To learn more about OHSUMED dataset, visit [Carnegie Mellon University](http://boston.lti.cs.cmu.edu/classes/95-865-K/HW/HW2/).

#### ohsumed-allcats.csv

| class | text |
| - | - |
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
  --data_csv ohsumed-allcats.csv \
  --model_definition_file model_definition.yaml
```

### Predict

```shell
$ ludwig predict \
  --data_csv ohsumed-allcats.csv \
  --model_path results/experiment_run/model/
```

### Experiment (Train and Predict)

```shell
$ ludwig experiment \
  --data_csv ohsumed-allcats.csv \
  --model_definition_file model_definition.yaml
```

## Epinions.com

### Dataset

Epinions.com is a website where people can post reviews of products and services. It covers a wide variety of topics. For this homework assignment, we downloaded a set of 12,000 posts about digital cameras and cars.

epinions contains a directory with two csv files

- Car category: epinions-1.csv. This dataset contains 6,000 messages. 50% are about automobiles. 50% are about another topic.
- Ford category: epinions-2.csv. This dataset contains 6,000 messages. 50% are about Ford automobiles. 50% are about other automobiles.

To learn more about Epinions.com dataset, visit [Carnegie Mellon University](http://boston.lti.cs.cmu.edu/classes/95-865-K/HW/HW2/).

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