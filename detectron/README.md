# Finetuning Detectron2

This example shows how to finetune a Detectron network to segment balloons in images. The script `detectron2_finetuning.py` is a simplified version of the [Detectron Colab tutorial](https://colab.research.google.com/drive/16jcaJoc6bCFAQ96jDe2HwtXj7BMD_-m5).

### Clone the example repo
```
git clone https://github.com/nimbo-sh/nimbo-examples.git
cd nimbo-examples/detectron
```

Copy your your key pair .pem file to this directory and replace any necessary values in the `nimbo-config.yml` file with your own credentials and preferences.

Replace the `my-bucket-name` in the `s3_results_path` and `s3_datasets_path` with your bucket.

Do not change the `local_results_path` and the `conda_env`, as they are already correctly set to match the runner script configuration.

#### Finetune the network
```
nimbo run "python -u detectron2_finetuning.py"
```

#### Download the results and saved models
```
nimbo pull results
```
