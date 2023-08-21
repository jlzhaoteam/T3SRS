# T3SRS
a Transformer model based on tensor train networks



## Usage

### 1. Download dataset

Download corresponding datasets into some directory, such as `./roughs`.

For [Steam](https://cseweb.ucsd.edu/~jmcauley/datasets.html#steam_data) dataset, use version 2.

Rename datasets: `'ml1m'` for MovieLens-1M, `'ml20m'` for MovieLens-2M, `'steam2'` for Steam.

### 2. Run

See default configuration setting in `entry.py`.

To modify configuration, make some directory under `runs/` like `./runs/ml1m/bert4rec/vanilla/`, and create `config.json`.

#### Sample Run Script

My `x0.sh` file that uses GPU No. 0:

```bash

python entry.py ml1m/bert4rec/vanilla


```

## Terminologies

The `df_` prefix always means DataFrame from Pandas.

* `uid` (str|int): User ID (unique).
* `iid` (str|int): Item ID (unique).
* `sid` (str|int): Session ID (unique), used only for session separation.
* `uindex` (int): mapped index number of User ID, 1 ~ n.
* `iindex` (int): mapped index number of Item ID, 1 ~ m.
* `timestamp` (int): UNIX timestamp.

## Data Files

After preprocessing, we'll have followings in each `data/:dataset_name/` directory.

* `uid2uindex.pkl` (dict): {`uid` &rightarrow; `uindex`}.
* `iid2iindex.pkl` (dict): {`iid` &rightarrow; `iindex`}.
* `df_rows.pkl` (df): column of (`uindex`, `iindex`, `sid`, `timestamp`), with no index.
* `train.pkl` (dict): {`uindex` &rightarrow; [list of (`iindex`, `sid`, `timestamp`)]}.
* `valid.pkl` (dict): {`uindex` &rightarrow; [list of (`iindex`, `sid`, `timestamp`)]}.
* `test.pkl` (dict): {`uindex` &rightarrow; [list of (`iindex`, `sid`, `timestamp`)]}.
* `ns_random.pkl` (dict): {`uindex` -> [list of `iindex`]}.
* `ns_popular.pkl` (dict): {`uindex` -> [list of `iindex`]}.

## Code References

* [theeluwin/session-aware-bert4rec](https://github.com/theeluwin/session-aware-bert4rec)

