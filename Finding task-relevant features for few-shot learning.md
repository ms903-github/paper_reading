# Finding task-relevant features for Few-shot learning by category traversal  

## 概要  
CVPR2019に投稿されたfew-shot learningの論文.
ドメイン適応ではなく，そもそも訓練データが一クラスあたりfew shot(1~5枚)しかないという問題設定．  
相当難しそうであり，正直精度はいまひとつだが面白そうな研究．  

## 背景・提案手法 
few-shot learningの手法として距離学習の枠組みが用いられている．  
距離学習では，学習用のサンプルデータsと分類を行いたい質問データqがあった時に，その特徴量間の距離を求めてqがsのクラスのうちどれに最も近いかを判別する．  
しかし，既存の手法では下図(a)のようにsのサンプルに対して個別にqのデータとの比較を行なっており，カテゴリ間での情報共有がなされていない．  
<img src = "https://github.com/ms903-github/pictures/blob/master/IMG_BC45846EE941-1.jpeg" width = "320px">  
そこで，上図(b)のようにcategory traversalネットワークを挟む．これは，あるサンプルが与えられた時に特徴量のうちどの次元に注目すべきかを出力する．
特徴量のうちの注目すべき次元というのは，例えば下図(a)のようにcolor, shapeの二次元の特徴量がある時にQuery exampleのどの特徴量を見てクラス判別を行うべきかということである．　　
<img src = "https://github.com/ms903-github/pictures/blob/master/IMG_B23EBDAF854C-1.jpeg" width = "320px">  
上図(b)は訓練データが一クラスあたり複数ある時の処理の説明．複数のサンプルがある場合はその全てを並列に考慮し，最も共通部分が多い特徴量次元を注目すべき次元とする．  
category traversalネットワークの詳細については省略するが，複数のCNNからなっている．  

## 実験結果  
![表1](https://github.com/ms903-github/pictures/blob/master/IMG_BB717088CD98-1.jpeg)  
ImageNetの一部を取りだし，5クラスおよび20クラス分類問題を解かせた時の分類精度．  
訓練データが1-shotおよび5-shotの場合で検証している．  

## 所感
1-shotのデータで20クラス分類問題が20%の精度ってすごいことだと思う．  
とはいえ，実用にはまだまだ不十分な感じかな.. 
特徴量抽出(最初の図の左のブロック)は学習済みモデルを使っていたりするのか？そこらへんがよくわからなかった．  
