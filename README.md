# fse22_prompt
anonymous repo for fse2022

In this repo we upload all of three tasks which are also can be introduced in detail at CodeXGlue.
## Defect Detection
Firstly download the dataset.
```bash
cd dataset
pip install gdown
gdown https://drive.google.com/uc?id=1x6hoF7G-tSYxg8AFybggypLZgMGDNHfF
cd ..
```
We provide prompt version and fine-tuning version.

To prompt tuning a CodeBERT, just 
```bash
cd defect/prompt
python codebert.py
```
To prompt tuning a CodeT5:
```bash
cd defect/prompt
python prompt_t5_2.py --visible_gpu <GPU> --data_dir=../dataset --max_source_length 512 --max_target_length 3 
```
To fine-tune a CodeT5, we provide the official and our implementation of CodeT5 repo in
```bash
cd defect/finetune
```

## Code Summarization
Download the dataset, where {LANG} can be one of six programming languages.
```bash
cd summarization/data
wget https://s3.amazonaws.com/code-search-net/CodeSearchNet/v2/{LANG}.zip
unzip {LANG}.zip
python preprocess.py
```
To fine-tune or prompt tuning CodeT5:
```bash
cd summarization
python finetune_t5_gene.py --visible_gpu <GPU> --lang {LANG} --max_source_length 256 --max_target_length 128 --log_name=./log/{LANG}.log
```

For prompt tuning, use prompt_t5.py

## Code Translation
Download dataset from CodeXGlue dataset:
```bash
cd translation/data
python preprocess.py
```
The runnning command is similar with code summarization for fine-tune and prompt tuning.