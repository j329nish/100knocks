# 言語処理100本ノック

| 章番号 | 内容                                | Colab | Link |
|--------|-------------------------------------|--------|--------|
| 第1章  | 準備運動                            | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j329nish/100knocks/blob/main/chapter1.ipynb)| [Link](https://github.com/j329nish/100knocks/blob/main/chapter1.ipynb) |
| 第2章  | UNIXコマンド                        | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j329nish/100knocks/blob/main/chapter2.ipynb)| [Link](https://github.com/j329nish/100knocks/blob/main/chapter1.ipynb) | [Link](https://github.com/j329nish/100knocks/blob/main/chapter2.ipynb) |
| 第3章  | 正規表現                            | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j329nish/100knocks/blob/main/chapter3.ipynb)| [Link](https://github.com/j329nish/100knocks/blob/main/chapter1.ipynb) | [Link](https://github.com/j329nish/100knocks/blob/main/chapter3.ipynb) |
| 第4章  | 形態素解析                          | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j329nish/100knocks/blob/main/chapter4.ipynb)| [Link](https://github.com/j329nish/100knocks/blob/main/chapter1.ipynb) | [Link](https://github.com/j329nish/100knocks/blob/main/chapter4.ipynb) |
| 第5章  | 大規模言語モデル                    | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j329nish/100knocks/blob/main/chapter5.ipynb)| [Link](https://github.com/j329nish/100knocks/blob/main/chapter1.ipynb) | [Link](https://github.com/j329nish/100knocks/blob/main/chapter5.ipynb) |
| 第6章  | 単語ベクトル                        | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j329nish/100knocks/blob/main/chapter6.ipynb)| [Link](https://github.com/j329nish/100knocks/blob/main/chapter1.ipynb) | [Link](https://github.com/j329nish/100knocks/blob/main/chapter6.ipynb) |
| 第7章  | 機械学習                            | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j329nish/100knocks/blob/main/chapter7.ipynb)| [Link](https://github.com/j329nish/100knocks/blob/main/chapter1.ipynb) | [Link](https://github.com/j329nish/100knocks/blob/main/chapter7.ipynb) |
| 第8章  | ニューラルネット                    | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j329nish/100knocks/blob/main/chapter8.ipynb)| [Link](https://github.com/j329nish/100knocks/blob/main/chapter1.ipynb) | [Link](https://github.com/j329nish/100knocks/blob/main/chapter8.ipynb) |
| 第9章  | 事前学習済み言語モデル（BERT型）    | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j329nish/100knocks/blob/main/chapter9.ipynb)| [Link](https://github.com/j329nish/100knocks/blob/main/chapter1.ipynb) | [Link](https://github.com/j329nish/100knocks/blob/main/chapter9.ipynb) |
| 第10章 | 事前学習済み言語モデル（GPT型）     | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/j329nish/100knocks/blob/main/chapter10.ipynb)| [Link](https://github.com/j329nish/100knocks/blob/main/chapter1.ipynb) | [Link](https://github.com/j329nish/100knocks/blob/main/chapter10.ipynb) |

(第4章まで)自然言語処理100本ノック 2020 [[URL](https://nlp100.github.io/2020/ja/)]<br>
(第5章から)自然言語処理100本ノック 2025 [[URL](https://nlp100.github.io/2025/ja/)]<br>

## 第9章まで終了済み

## 備忘録

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
- 一行ずつ処理することが多いため、辞書型リストdict[list]よりもリスト型の辞書list[dict]の方が使いやすい。
- 機械学習でepochごとに処理をするとき、tqdmで進捗状況が分かる。
  ```python
  from tqdm import tqdm
  for i in tqdm(range(10)):
    continue
  ```
  ```bash
  100%|██████████| 10/10 [00:00<00:00, 30437.62it/s]
  ```
- torch, numpy, scikit-learn, transformersのライブラリの使い方を熟知していれば後半は簡単そう。
- matplotlibは覚えておいた方が良い。日本語を使いたいならjapanize_matplotlibがある。


(最終更新 2025/4/27)
