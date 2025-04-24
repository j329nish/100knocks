# 第4章まで

自然言語処理100本ノック 2020

# 第5章から

自然言語処理100本ノック 2025 [[URL](https://nlp100.github.io/2025/ja/ch05.html)]

# 第9章85まで終了済み

# 備忘録

- 出力を綺麗にしたいならpprintが良き。
  ```python
  from pprint import pprint
  pprint(data)
  ```
- ファイルは基本wgetでとってくる。zipファイルなら、unzipして、rmでzipファイルを削除しておく。-Pで保存先の指定が可能。
  ```python
  # ファイルのインポート例
  !wget https://dl.fbaipublicfiles.com/glue/data/SST-2.zip -P data/
  !unzip -o data/SST-2.zip -d data/
  !rm data/SST-2.zip
  ```
- データフレームを使うならpandasが圧倒的に楽。処理が遅いため、大規模なデータならdatasetsの方が良い。
  ```python
  # pandas
  import pandas as pd
  df = pd.read_csv("data.csv")

  # datasets
  from datasets import load_dataset
  dataset = load_dataset('glue', 'sst2')
  print(dataset)

  # pandas -> datasets
  from datasets import Dataset
  dataset = Dataset.from_pandas(df)
  ```
- matplotlibは覚えておいた方が良い。日本語を使いたいならjapanize_matplotlibがある。


(最終更新 2025/4/25)
