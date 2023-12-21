# 応用プロジェクト 2023 評価コード

## Contents

- `input_gen.ipynb`
  - 目標水圧(mbar)のファイルを生成します
- `score.ipynb`
  - `print_result(df_result:pd.DataFrame, df_target:pd.DataFrame)`で結果シートが出力されます。
    - kwargs オプション
      - `dir_out`; defaults to `'./output/'`
      - `filename`; defaults to `datetime.datetime.now().strftime("%Y-%m-%d %H%M%S")`
    - `df_result`は以下の通りにデータ列が並んでいれば正常に処理されます（カラム名は問いません）
  ```
  [
    "time",
    "acc_x",
    "acc_y",
    "acc_z",
    "pitch",
    "roll",
    "yaw",
    "pressure",
    "flag",
  ]
  ```

## 実行環境

- Python 3.9
  - numpy
  - pandas
  - matplotlib
  - pathlib
  - datetime
