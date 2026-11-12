 Datasets

Nothing is stored in this repo. Data downloads on demand via kagglehub and
caches under ~/.cache/kagglehub/.

## Access

Requires a Kaggle account and credentials. In a notebook:

    import kagglehub
    kagglehub.login()

For GiveMeSomeCredit you must also click "Join Competition" on the website
before the API will serve the files.

## Give Me Some Credit

    kagglehub.competition_download('GiveMeSomeCredit')

- Source: https://www.kaggle.com/c/GiveMeSomeCredit
- Files: cs-training.csv (150,000 rows, labelled), cs-test.csv (unlabelled,
  not usable for evaluation), sampleEntry.csv, Data Dictionary.xls
- Target: SeriousDlqin2yrs — borrower went 90+ days delinquent
- Licence: Kaggle competition rules. Not for redistribution.
- Used in: weeks 1-6 (ISL topics), week 15 (trees and boosting)

## Cookie Cats

    kagglehub.dataset_download('yufengsui/mobile-games-ab-testing')

- Source: https://www.kaggle.com/datasets/yufengsui/mobile-games-ab-testing
- Files: cookie_cats.csv (~90,189 rows)
- Columns: userid, version (gate_30 | gate_40), sum_gamerounds,
  retention_1, retention_7
- Licence: see the dataset page
- Used in: Project 1, the A/B test analysis
