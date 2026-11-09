# Frozen-feature experiment

Use Python 3.10 or newer with the packages in `requirements_v6.txt`. A CUDA-enabled PyTorch installation accelerates feature extraction; CPU extraction is also supported with `--device cpu --batch-size 1`. The classification notebook runs on CPU once features have been extracted.

Place the original competition CSV files in `data/`. Download the fixed checkpoint and extract label-free features:

```bash
python frozen_lm_features.py --download --data data
python frozen_lm_features.py --data data --output lm_features/gpt2 --batch-size 8
```

The first command downloads model/tokenizer files into `model_cache/`. The second command uses only cached model files and runs locally. It writes feature tables and input hashes for train, unlabeled and test passages. No passage text is sent to an external API. The model processes at most 511 passage tokens plus BOS and stays frozen.

Run all cells of `svm_frozen_lm_yx752_v6.ipynb` to reproduce the seed-27 split, training-only OOF comparisons, fixed development evaluation and full-data predictions. An existing v5 OOF cache is optional; otherwise the baseline OOF scores are recomputed. The final cell writes `v6_results/submission_yx752_v6.csv`.

The checkpoint name is `openai-community/gpt2`. All supervised labels come from the supplied `train.csv`; additional labeled datasets are not used.
