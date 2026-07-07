# MovieLens K-means クラスタリング

映画評価データを用いて、K-means法によりユーザーを嗜好グループに分類する分析プログラムです。

## 概要

MovieLens ml-32m データセットから抽出した50ユーザー×8映画の評価データに対して前処理を施し、K-meansクラスタリングによってユーザーの映画嗜好パターンを3グループに分類しました。

## 使用データ

**MovieLens 32M Dataset**  
提供元：GroupLens Research（ミネソタ大学）  
URL：https://grouplens.org/datasets/movielens/

> ⚠️ ライセンスの都合上、データファイルは本リポジトリに含まれていません。  
> 上記URLから `ml-32m.zip` をダウンロードし、解凍後に `ratings.csv` と `movies.csv` を使用してください。

## ファイル構成

```
.
├── movielens_kmeans.ipynb   # メインのJupyter Notebook
├── README.md
└── .gitignore
```

## 前処理の内容

1. **ユーザーの選別** - 評価件数上位50人を抽出
2. **映画の選別** - 評価件数上位8本を抽出
3. **評価行列の作成** - 50×8のピボットテーブルを作成（欠損率1.5%）
4. **欠損値補完** - 各ユーザーの平均評価値で補完
5. **標準化** - StandardScalerで平均0・分散1に正規化

## 実行環境

- Python 3.x
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```

## 実行方法

1. MovieLensデータを入手し、前処理スクリプトを参考に `movielens_50users.csv` を作成する
2. Jupyter Notebookを起動する
3. `movielens_kmeans.ipynb` を開いてセルを順番に実行する

## 結果

| クラスタ | 人数 | 特徴 |
|---|---|---|
| Cluster 0 | 24人 | Pulp Fiction・Shawshank Redemptionを高評価 |
| Cluster 1 | 5人 | Star Warsを好む層 |
| Cluster 2 | 21人 | Pulp Fiction・Alienを特に高評価する熱狂的な層 |
