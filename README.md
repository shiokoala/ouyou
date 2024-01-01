# 応用プロジェクト 2023 評価コード

## Contents

- `input_gen.ipynb`
  - 目標水圧(mbar)のファイルを生成します。
  - 12/28二宮追記 評価方法の変更のため今は使っていません
- `score.ipynb`
  - 演目1の評価プログラム
  - `set_initial_value`の項目で目標深度p1,p2を設定する。またtime_devidedに深度を切り替えた時間を記載する。time_devideの前のデータでp1の値をとれているか評価し、time_devidedの後のデータでp2の値をとれているか評価する
  - `time_devided`でデータを2つにわり、それぞれp1、p2の値に一番近い値をとれるような10sを抽出する
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
- `score2.ipynb`
  - 演目2の評価プログラム
  - ターゲットの値をy=p1 + bias + Asin(2pi t/T)で定義し、二乗誤差で比較する
  - ターゲットのサイン関数の振幅、周期、p1はset initial value で定義する
  - biasを変化させて二乗誤差が最小となるようfittingを行い、その時の二乗誤差の値とbiasを出力する

- `score3.ipynb`
  - 演目3の評価プログラム
  - set initial valueで目標深度p1を設定する
  - 最も二乗誤差平均が小さくなる30s間を自動的に抽出する

## 実行環境

- Python 3.9
  - numpy
  - pandas
  - matplotlib
  - pathlib
  - datetime
