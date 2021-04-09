# Train a neural network on MNIST with Pytorch 1.6


```
# Clone the examples repo
git clone https://github.com/nimbo-sh/nimbo-examples.git
cd nimbo-examples/pytorch-mnist

# Download MNIST to the local folder
mkdir -p data/datasets
wget www.di.ens.fr/~lelarge/MNIST.tar.gz -O data/datasets/MNIST.tar.gz
tar -zxvf data/datasets/MNIST.tar.gz -C data/datasets
rm data/datasets/MNIST.tar.gz

# Upload MNIST to your S3 datasets folder bucket
# Make sure that s3_datasets_path and s3_results_path are correctly set in nimbo-config.yml
nimbo push datasets

# Train a neural network
nimbo run "python -u train.py --epochs=5 --save-model --log-interval=100"

# Pull the results and saved model to your computer
nimbo pull results

# If you just want to pull the logs, use
nimbo pull logs
```
