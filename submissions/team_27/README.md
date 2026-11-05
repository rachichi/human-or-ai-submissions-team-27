**Team members:** Rachel Liu (rl996), Henry Lam (hgl32), Yang Xiao (yx752)  
**Kaggle team name:** `team-27`

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Place the Kaggle data files (`train.csv`, `unlabeled.csv`, `test.csv`) in `./data/` (not committed).

## Train / validate

```bash
python train.py --train data/train.csv --seed 20261023
```

## Predict (writes Kaggle submission)

```bash
python predict.py --test data/test.csv --out submission.csv
```

## Transformer experiment

Run `transformer_all.ipynb` to fine-tune DistilRoBERTa, evaluate on the shared stratified 2,000-row development split, then refit on all labeled rows and write `submission_transformer.csv`.

## Seeds and notes

- Notebook split seed: `27` (shared by the model comparison notebooks)
- `train.py` default seed: `20261023`
- Validation: stratified 2,000-row holdout from `train.csv`, fixed across comparisons

## AI assistance

Briefly describe tools used and what you verified manually (required for Q6.3).
