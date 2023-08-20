---
title : Tensorflow Serving
notetype : feed
date : 18-01-2022
---


> **Summary**
> - Tensorflow Serving can **poll updated model automatically**
> - Tensorflow Serving can **poll from Cloud Storage (e.g. AWS, GCP)**
> - Tensorflow Serving can **deploy multiple models, or multiple model’s version**
> - Tensorflow Serving **support batch inference requests**




## Deploy model with Tensorflow Serving

```shell
docker run -p 8500:8500 \
           -p 8501:8501 \
           --mount type=bind, source=/tmp/models, target=/models/my_model \
           -e MODEL_NAME=my_model \
           -e MODEL_BASE_PATH=/models/my_model \
           -t tensorflow/serving
```

### 1 Model Polling


Tensorflow serving has an option called `file_system_poll_wait_seconds` which try to poll the files within the specific interval.

```shell
docker run ... \
           --file_system_poll_wait_seconds=3600
```


### 2 Remote files

We can hosted the model files, along with other configuration files in the Cloud Storage (e.g. AWS, GCP)

#### 2.1 Amazon Web Service (S3)



```shell
docker run ... \
           -e MODEL_PATH=s3://.... \
           -e AWS_ACCESS_KEY_ID=xxx \
           -e AWS_SECRET_ACCESS_KEY=xxx \
           -e AWS_REGION=xxx
```


#### 2.2 Google Cloud Platform (Google Cloud Storage)


```shell
docker run ... \
           -e MODEL_PATH=gs://... \
           -e GOOGLE_APPLICATION_CREDENTIALS=path/to/credentials.json
```


## 3 Model Configuration

There are a several configuration we can play around with. What we should do is create the file for configuration (e.g. named model_config_list) and use it when running Tensorflow serving

```shell
docker run ... \
           --model_config_file=gs://...../model_config_list
           --model_config_file_poll_wait_seconds=3600
```


Within the file named model_config_list we can specify different configuration.


### 3.1 Deploy multiple models


```txt
model_config_list {
  config {
    name: 'my_first_model'
    base_path: 'gs://.../my_first_model'
    model_platform: 'tensorflow'
  }
  config {
    name: 'my_second_model'
    base_path: 'gs://.../my_second_model'
    model_platform: 'tensorflow'
  }
}
```


### 3.2 Deploy multiple model's versions


```txt
model_config_list {
  config {
    name: 'my_first_model'
    base_path: 'gs://.../my_firist_model'
    model_version_policy {
      specific {
        versions: 1556250435
        versions: 1556251435
      }
    }
  }
}
```

#### 3.2.1 Version labels

```txt
model_config_list {
  config {
    name: 'my_first_model'
    base_path: 'gs://.../my_firist_model'
    model_version_policy {
      specific {
        versions: 1556250435
        versions: 1556251435
      }
    }
    version_labels {
      key: 'stable'
      value: 1556250435
    }
    version_labels {
      key: 'testing'
      value: 1556251435
    }
  }
}
```

Then client can call to different model version by specifying the model labels, versions, and model name

**REST Usage**

With version number

```txt
v1/models/<model_name>/versions/<version_number>
```

With version label

```txt
v1/models/<model_name>/versions/<version_label >
```

Read more in [Tensorflow serving official document](https://www.tensorflow.org/tfx/serving/serving_config#model_server_configuration).


## 4. Batching inference requests


```shell
docker run ... \
           --enable_batching=true
           --batching_parameters_file=gs://..../batching_parameters.txt
```


Within the `batching_parameters.txt` you can just write down the configuration


```txt
max_batch_size { value: 32 }
batch_timeout_micros { value: 5000 }
pad_variable_length: true

```


#tensorflow #machine-learning