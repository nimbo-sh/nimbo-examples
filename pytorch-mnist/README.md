# Train a neural network on MNIST with Pytorch 1.6

#### Clone the examples repo
```
git clone https://github.com/nimbo-sh/nimbo-examples.git
cd nimbo-examples/pytorch-mnist
```
Copy your your key pair .pem file to this directory and replace any necessary values in the nimbo-config.yml file with your own credentials and preferences.

Replace the my-bucket-name in the `s3_results_path` and `s3_datasets_path` with your bucket.

Do not change the `local_results_path` and the `conda_env`, as they are already correctly set to match the runner script configuration.

#### Download MNIST to the local folder
```
mkdir -p data/datasets
wget www.di.ens.fr/~lelarge/MNIST.tar.gz -O data/datasets/MNIST.tar.gz
tar -zxvf data/datasets/MNIST.tar.gz -C data/datasets
rm data/datasets/MNIST.tar.gz
```

#### Upload MNIST to your S3 datasets folder bucket
Make sure that `s3_datasets_path` and `s3_results_path` are correctly set in your `nimbo-config.yml`.
```
nimbo push datasets
```

#### Train the neural network on EC2
```
nimbo run "python -u train.py --epochs=5 --save-model --log-interval=100"
```

#### Sync the results and saved model into your computer
```
nimbo pull results
```

If you just want to get the logs, use:
```
nimbo pull logs
```

If you are not happy with the results, delete some of the contents in `local_results_path` (e.g. the model weights) and update the `s3_results_path` by running:
```
nimbo push results --delete
```
