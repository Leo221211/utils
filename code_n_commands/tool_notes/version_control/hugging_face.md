## 1. install & authenticate etc

```
pip install huggingface_hub
hf login
```

## 2. Create repo

Via UI, or

```
hf repo create my-dataset --type dataset
hf repo create my-dataset --type dataset --private
```

## 3. Sync

1. Pull

    **Note**: the hf pull will directly overwrite (?)
    ```
    # Download entire dataset to a specific local folder
    hf download <username/my-dataset> --repo-type dataset --local-dir ./my-local-data

    # Download specific files only (e.g., only parquet files)
    hf download <username/my-dataset> --repo-type dataset --include "*.parquet" --local-dir ./my-local-data
    ```

1. Push
    ```
    # Upload an entire local folder to the dataset repo
    hf upload <username/my-dataset> ./my-local-data --repo-type dataset

    # Upload a specific file to a specific path in the repo
    hf upload <username/my-dataset> ./local_data.csv "data/raw_data.csv" --repo-type dataset

    # Upload and delete files in the remote repo that don't exist locally (mirroring)
    hf upload <username/my-dataset> ./my-local-data --repo-type dataset --delete

    ```

1. Notes
    1. `--repo-type`: default is `model`, if it is dataset, set it to dataset because the logicc might be different.