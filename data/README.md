# Data

Raw and processed datasets are intentionally excluded from version control. Download the datasets directly from Kaggle and check their terms of use before working with or redistributing them.

## Prerequisites

1. Create or sign in to a Kaggle account.
2. Accept any competition or dataset rules required by Kaggle.
3. Configure the Kaggle API. The standard setup is to download `kaggle.json` from the Kaggle account settings page and place it in the location expected by the Kaggle CLI. Do not commit this file.
4. From the repository root, create `data/raw/` and place each downloaded dataset in its own subdirectory.

## Potential Datasets

### ULB Credit Card Fraud Detection

Dataset page: <https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud>

```bash
kaggle datasets download -d mlg-ulb/creditcardfraud -p data/raw/ulb_credit_card --unzip
```

The main file is typically `creditcard.csv`, with `Class` as the fraud label.

### IEEE-CIS Fraud Detection

Competition page: <https://www.kaggle.com/competitions/ieee-fraud-detection>

```bash
kaggle competitions download -c ieee-fraud-detection -p data/raw/ieee_cis
```

Unzip the downloaded archive into `data/raw/ieee_cis/`. The data is split across transaction and identity files. The target is typically `isFraud` in the training transaction data. Competition access and rules may be required.

### PaySim

Dataset page: <https://www.kaggle.com/datasets/ealaxi/paysim1>

```bash
kaggle datasets download -d ealaxi/paysim1 -p data/raw/paysim --unzip
```

The main file is typically `PS_20174392719_1491204439457_log.csv`, with `isFraud` as the fraud label.

## Data Handling

Do not use fraud labels while fitting an anomaly detector. Keep a separate evaluation copy of the labels and merge them only after predictions or anomaly scores have been produced. Inspect for direct leakage, identifiers, duplicated rows, and post-outcome fields before training. Document any filtering, encoding, scaling, sampling, or missing-value treatment in the relevant notebook.

The exact filenames and schemas may change, so verify downloaded files against the dataset page before running experiments.