# Train a neural network on MNIST with Tensorflow 2.2, on a spot instance

#### Clone the examples repo
```
git clone https://github.com/nimbo-sh/nimbo-examples.git
cd nimbo-examples/tensorflow-mnist
```
Copy your your key pair .pem file to this directory and replace any necessary values in the nimbo-config.yml file with your own credentials and preferences.

Replace the my-bucket-name in the `s3_results_path` and `s3_datasets_path` with your bucket.

Do not change the `local_results_path` and the `conda_env`, as they are already correctly set to match the runner script configuration.

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
