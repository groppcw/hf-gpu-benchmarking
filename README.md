# hf-gpu-benchmarking
Replication code and settings for benchmarking HuggingFace Transformers.


The following settings and parameters represent what was used for the final benchmarking runs described in the body of the paper, and are presented here for replication information; other software versions, settings, and so forth were experimented with during the troubleshooting process.

## Key software libraries:
    * HuggingFace Transformers 4.32.1
    * PyTorch 2.1.1
    * Python 3.11.5
    * CUDA 12.1
    * Ray 2.9.1

## Model training information and parameters:

    * Pretrained model: "bert-base-uncased" from transformers AutoModelForSequenceClassification
    * Tokenizer: "bert-base-uncased" from transformers autotokenizer
    * Labels: 2
    * Training validation set: 20% holdout of training set, chosen randomly but consistent between test runs
    * Epochs: 3
    * Warmup steps: 500
    * Weight decay: 0.01


## Data preprocessing steps:
    * Dataset: IMDB Movie Reviews Dataset published by IEEE Dataport
    * Remove reviews without rating scores or descriptions
    * Concatenate review title (user-provided, not the movie title itself) and description to form the input text
    * Label ratings 5 or less as ``negative'', 6 or higher as ``positive''
    * 20% of data held out as an evaluation set, not to be used during training

## SLURM execution and modifications for parallelism
As noted in the body of the paper, we struggled to locate specific information on basic configuration steps within the wealth of detailed documentation. We here include the key function calls, in the hope that they may be useful to others.

TODO - SLURM flags
TODO - srun
TODO - torch load necessary flags
TODO - torch init
TODO - torch push onto/pull from GPUs
