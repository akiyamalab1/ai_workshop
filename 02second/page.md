# ニューラルネットワークについて
<br>
<br>

## AIの歴史
<br>
![AIの歴史](http://www.soumu.go.jp/johotsusintokei/whitepaper/ja/h28/image/n4201050.png)
[総務省より](http://www.soumu.go.jp/johotsusintokei/whitepaper/ja/h28/html/nc142120.html)
<br>
<br>
第1次.AIの考え方が生まれた(パーセプトロン,ニューラルネットワーク)  
第2次.AIが実用可能になった(特定の分野)  
第3次.AIの応用先が劇的に広がった(ビッグデータ)  
<br><br>
![nyu-ron](https://www.jst.go.jp/pr/announce/20150122/icons/zu1.gif)
<br>
脳の神経回路がニューロンと呼ばれ、これをモデルにしたものが  
パーセプトロンです。  

## パーセプトロン
<br>
![aa](./images/perceptron.png)
<br>
パーセプトロンとは、複数の信号を入力として受け取り、  
ひとつの信号を出力するもの。  
脳のニューロンを模しています。
<br>

## 重み
<br>
![omomi](./images/omomibias.png)
<br>
重みとは入力の値に掛け算をするものです。  
入力の特徴を強くする。  
↓上の図を式にしたもの  
![weight](./images/weight.png)
<br>
y:出力 w:重み x:入力 b:バイアス(底上げ)
<br>

## ニューラルネットワーク
<br>
![mlp](./images/mlp.png)
<br>
パーセプトロンを複数にしたもの。マルチパーセプトロンともいう。  
複雑な計算ができる。  
<br>

## 実際にニューラルネットワークを作ろう
実装のモデルとして論理回路を使います。  
論理回路とは、複数の入力の値からひとつの出力を出すものです。  
上のパーセプトロンと同じ感じがします。  
身近なもので、照明のスイッチがあげられます。  
![ronri](./images/ronnri.png)
<br>
<br>
ではコマンドプロンプトを開きましょう。  
homeボタンを押して、cmdと入力してEnterキーを押しましょう。  
場所を移動しましょう。cd Desktop で作業の場所をデスクトップにします。  
```
C:\User>cd Desktop\

C:\User\Desktop>
```
デスクトップには kouza10-26 というフォルダがあります。ここに移動します。
```
C:\User\Desktop>cd kouza10-26

C:\User\Desktop\kouza10-26>
```
ここでPythonスクリプト(プログラム)を作ります。  
メモ帳を開きましょう。  
まず、論理回路のAND回路を作ります。  
```python
def AND(x1, x2):
  if x1 == 1 and x2 == 1:
    return 1#入力の両方が1なら1を返す
  else:
    return 0#それ以外に0を返す
```
保存するときはファイルの種類を すべてのファイル に指定して、  
logic.py という名前で保存します。  
今作ったものを使ってみましょう。  
cmdで python と入力しましょう。  
```
C:\User\Desktop\kouza10-26>python
Python 3.7.3 ~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
>>> from logic import *
>>> AND(0,0)
0
>>> AND(1,0)
0
>>> AND(0,1)
0
>>> AND(1,1)
1
>>> exit()
```
AND回路の真理値表どおりになったと思います。  
次にOR回路を作ります。  
さっきの logic.py を開き続きを書きましょう。  
```python
def AND(x1, x2):
  if x1 == 1 and x2 == 1:
    return 1
  else:
    return 0

def OR(x1, x2):
  if x1 == 1 or x2 == 1:
    return 1#入力のどちらかが1なら1を返す
  else:
    return 0#それ以外に0を返す
```
さっきと同じように使ってみましょう。  
```
C:\User\Desktop\kouza10-26>python
Pthon 3.7.3~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
>>> from logic import *
>>> OR(0,0)
0
>>> OR(1,0)
1
>>> OR(0,1)
1
>>> OR(1,1)
1
>>> exit()
```
確認できたと思います。  
最後にNOT回路を作ります。  
同じようにlogic.pyに追記しましょう。  
```python
def AND(x1, x2):
  if x1 == 1 and x2 == 1:
    return 1
  else:
    return 0

def OR(x1, x2):
  if x1 == 1 or x2 == 1:
    return 1#入力のどちらかが1なら1を返す
  else:
    return 0#それ以外に0を返す

  def NOT(x):
    if x == 0:
      return 1#入力が0のとき1を返す
    else:
      return 0#入力が1のとき0を返す
```
使ってみましょう。  
```
C:\User\Desktop\kouza10-26>python
Pthon 3.7.3~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
>>> from logic import *
>>> NOT(1)
0
>>> NOT(0)
1
>>> x = OR(1,1) ←xにOR(1,1) = 1 を代入
>>> NOT(x)
0
>>> exit()
```
<br>
ニューラルネットワークとは上のほうで書いてあるとおり、  
複数のパーセプトロンを組み合わせたものです。  
論理回路でも複数の回路を組み合わせて  
作ることができる回路があります。  
XOR回路とは、入力がすべて同じなら0を返す回路です。
<br>
![xor](./images/xor_1.png)
<br>
<br>
なぜ複数のパーセプトロンが必要かというと、
XORが非線形だからです。  
OR回路をグラフで表すと、  
<br>
<br>
![or_graph](./images/orgraph.png)
<br>
<br>
になります。  
これは直線で1と0を分ける事ができるので、線形であると言えます。  
一方XORは直線で分けることができません。  
<br>
![xor_graph](./images/xor_graph.PNG)
<br>
<br>
なのでパーセプトロンを複数使うことでXORを実装することになります。
<br>
<br>
![xor](./images/xor.png)
<br>
<br>
↑がXOR回路です。今までの回路をもとにXORをpythonで作りましょう。  

↓答え<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
↓<br>
```python
def XOR(x1, x2):
  i1 = OR(x1, x2) #仮の入力を用意
  i2 = NOT(AND(x1, x2)) #i1とi2
  return AND(i1, i2)
```
試してみましょう。  
```
C:\User\Desktop\kouza10-26>python
Pthon 3.7.3~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
>>> from logic import *
>>> XOR(0,0)
0
>>> XOR(1,0)
1
>>> XOR(0,1)
1
>>> XOR(1,1)
0
>>> exit()
```
これでこの章は終わります。  
パーセプトロンの考え方はわかったと思います。  
また、中間層を作ることで表現力が上がることがわかりました。
<br>
<br>
[前へ](../01first/page.md)・[次へ](../03third/page.md)
<br>
<br>
[HOME](../index.md)
