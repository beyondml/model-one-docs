# Model One python wrapper

[Model One](https://beyond.ml/model-one) is a few-shot AutoML system.

Model One can do almost anything that requires understanding or generating natural language. Model One is able to solve tasks in 12 languages: English, Spanish, Portuguese, Russian, Turkish, French, German, Italian, Arabic, Polish, Dutch, and Hebrew.

This package provides a simple wrapper for using our api.

Using `model-one` package allows you to train and apply models.

## Get started

Firstly fill out the [form](https://beyond.ml/model-one#rec435480002) to get a key to access the API. We will send you the key within a day.

### Install
To install the package just use `pip --install model-one`.

### Usage

```py
import beyondml
import pandas as pd

beyondml.api_key = 'YOUR_API_KEY'

# create a model
model = beyondml.create_generative()

# save the model for further usage
model.save('filename.bml')
# if you want to load
model = beyondml.load('filename.bml')

tdf = pd.read_csv('train.csv')
vdf = pd.read_csv('test.csv')

# upload datasets 
model.upload(tdf['inputs'], tdf['outputs'], vdf['inputs'], vdf['outputs'])
model.fit()

# wait...
# a few hours
# while our GPUs train your model
print(model.status())
print(model.ready())

# inference!
model.generate('The Answer to the Ultimate Question of Life, the Universe, and Everything')
```
