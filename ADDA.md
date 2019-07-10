# Adversarial Discriminative Domain Adaptation  
## 概要  
敵対的学習を用いたドメイン適応の様々なアルゴリズムを整理して最も良いものを提案している．　　
提案手法よりもadversarial domain adaptationの諸々の手法を俯瞰する枠組みを提案したことに意義がある気がする．

## 背景
敵対的学習を用いるドメイン適応の手法はCoGAN(二つのGAN構造を用いる)やDANN(GRLを用いる)など様々なものが提案されてきているが，それらの手法は下図のように俯瞰できる．
![図1](https://github.com/ms903-github/pictures/blob/master/IMG_6521A1872FBB-1.jpeg)  
例えば，DANN, Domain Confusion, coGANの手法は以下の表のようにまとめられる．  
![表1](https://github.com/ms903-github/pictures/blob/master/IMG_D59D4C50B0AF-1.jpeg)  
ADDAでは表に示すような組み合わせで適応を行うことを提案する．  

## 提案手法  
背景で提案したように，敵対的学習によるドメイン適応を  
- discriminative model(画像入力をうけて特徴量を生成する形式)  
- weight unshared(ソースのとターゲットの特徴量生成において重みを共有しない)  
- GANロスの使用(GANのように生成器学習⇄判別器学習を繰り返す)  
の三つの条件下で行う  
よって訓練の概要図は下図のようになる  
![図2](https://github.com/ms903-github/pictures/blob/master/IMG_65C4C30C4912-1.jpeg)  

## 実験結果  
MNIST, USPS, SVHN間のドメイン適応およびRGB画像-Depth画像間のドメイン適応を行い，DANNおよびDomain confusionの結果に比べていい成果を出した．  


