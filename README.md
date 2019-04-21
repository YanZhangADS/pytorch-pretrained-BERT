# PyTorch Pretrained BERT: The Big & Extending Repository of pretrained Transformers

Objective: To Make SST-2 Task run

## Prerequisites
- Ubuntu Linux with GPU

## Steps

### Get data



- Download data

```shell
wget https://gist.githubusercontent.com/W4ngatang/60c2bdb54d156a41194446737ce03e2e/raw/17b8dd0d724281ed7c3b2aeeda662b92809aadd5/download_glue_data.py

python download_glue_data.py
```

- Write down the directory where the data resides e.g. `/path/to/glue_data`

### Set up environment

- git clone https://github.com/YanZhangADS/pytorch-pretrained-BERT

- navigate into the repo

- conda env create -f environment.yml

- conda activate bert_env

- navigate into ./examples directory

- run following commands.

```shell
export GLUE_DIR=/path/to/glue_data
export TASK_NAME=SST-2

python run_classifier.py \
  --task_name $TASK_NAME \
  --do_train \
  --do_eval \
  --do_lower_case \
  --data_dir $GLUE_DIR/$TASK_NAME \
  --bert_model bert-base-uncased \
  --max_seq_length 128 \
  --train_batch_size 32 \
  --learning_rate 2e-5 \
  --num_train_epochs 3.0 \
  --output_dir /tmp/$TASK_NAME/ \
  --use_tensorboard
```
The dev set results will be present within the text file 'eval_results.txt' in the specified output_dir. In case of MNLI, since there are two separate dev sets, matched and mismatched, there will be a separate output folder called '/tmp/MNLI-MM/' in addition to '/tmp/MNLI/'.

