# text2query
The Pytorch implementation of RESDSQL on CoSQL dataset

## Prerequisites
Create virutal conda env
```bash
conda create -n <your_env_name> python=3.8.5
```

Active it and install the cuda version Pytorch:
```bash
conda install pytorch==1.11.0 torchvision==0.12.0 torchaudio==0.11.0 cudatoolkit=11.3 -c pytorch
```

Install other required modules and tools:
```bash
pip install -r requirements.txt
pip install https://github.com/explosion/spacy-models/releases/download/en_core_web_sm-2.2.0/en_core_web_sm-2.2.0.tar.gz
python nltk_downloader.py
```

## Training on CoSQL
```bash
# Step1: preprocess dataset
sh scripts/train/text2sql/preprocess.sh
# Step2: train cross-encoder
sh scripts/train/text2sql/train_text2sql_schema_item_classifier.sh
# Step3: prepare text-to-sql training and development set for T5
sh scripts/train/text2sql/generate_text2sql_dataset.sh
# Step4: (or) fine-tune T5-Base (RESDSQL-Base)
sh scripts/train/text2sql/train_text2sql_t5_base.sh
```
