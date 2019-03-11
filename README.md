# DataSciense

## Python

```python=
import pandas as pd // csvファイルを取り扱う
import numpy as np // 配列処理
from matplotlib import pyplot as plt // 図、表の挿入
%matplotlib inline // jupyter上で表の表示を行う
```

- pd.read_csv('filename'): csvファイルの読み込み。（option: header=Noneで列名(ヘッダー)のない状態に）

### trainに代入した場合、

- train[train['y'] >= 150]: yが150以上のもののみ
- train[['y', 'week']]: yとweekだけ列とする

### 関数

#### 視覚化

##### 表

- head, tail: 表の一部の表示（default: ５件）
- describe: 基本統計量（平均、最小最大値、中央値）
- shape: 表の行数、列数
- info: 型の確認
- value_counts: どの値がいくつあるのかの確認
- mean(): 平均値
- median(): 中央値(describeで代用可)
- sort_values(by = ''): 昇順（多）, option: ascending=false: 降順（少）

##### 図

- plot: 折れ線グラフの表示（figsize = (12, 4)）

```python=
// 時間軸をXにしたYの変化量のグラフを描画
ax = train['y'].plot(figsize = (12, 4), title = 'グラフ')
ax.set_xlabel('time')
ax.set_ylabel('y')
```

- plot.hist: ヒストグラム（option: grid）
- plt.axvline: 表に縦線を追加（option: x = 位置、color = '色(red)'）
- boxplot(by = 'week'): 箱ひげ図。二つ指定する( train[['y', 'week']] )。`by=`で横軸を指定。〇は外れ値。

#### 前処理

- 欠損値の個数: `isnull().sum()`, 有無だけなら`isnull().any()`
- fillna(number): Nanに対してnumberを代入
- dropna(): 欠損値があれば表示しない。option: `subset=['']`で列指定