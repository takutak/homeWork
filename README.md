## :computer: Get Started
#### Windows

Track-AnythingではNVIDIA製のGPU利用を前提としているが、私のパソコンにはNVIDIA製GPUが搭載されていない。（そのため、ローカル環境でapp.pyを実行すると、CUDAを認識できずエラーとなる。）
そのため、google colaboratory上でファイルを実行する。

#### 環境構築
新たにColab上でノートを作成し、ランタイムのタイプをGPUに変更する。その後本ディレクトリをアップロードする。
```
!git clone https://github.com/takutak/homeWork.git
```
その後、このアップロードしたディレクトリに移動
```
%cd homeWork
```
その後、以下コマンドによりrequirements.txtファイルを読み込む。
```
!pip install -r requirements.txt
```

#### 実行
```
!python app.py --device cuda:0
```
とコマンドをうち、app.pyを実行する。

実行後、Running on public URL: URL名
が表示されるので、URLをクリックすることで、プロジェクトを実行できる。

#### 操作
動画をアップロードし、Resize ratioを0.5以下の値に設定します（google colabのGPU上限対策）
その後、  Get video infoを押し、add maskを押した後、trackしたい対象をクリックし対象人物が変色する事を確認します。その後、trackingを押すと追跡処理が実行され、ビデオが生成されます。

#### VLogの環境構築
以下のコマンドをcolab上で新しいノートブックで実行する。
```
!git clone https://github.com/showlab/VLog.git
%cd VLog
%mkdir checkpoints
%cd checkpoints
!wget "https://datarelease.blob.core.windows.net/grit/models/gr
%cd ..
```
その後、以下のコマンドによりconda環境を構築する。
```
!pip install -q condacolab
import condacolab
condacolab.install()
```
```
!conda create -n vlog python==3.8
!conda init
!source activate vlog
```
この状態で、VLogディレクトリ上で以下のコマンドを実行する。
```
!pip install -r requirements.txt
```


---
#### 現在の問題点
colab環境でうまくcondaの仮想環境を設定することができない。
自前のPCだとCUDA環境のPyTorchをインストールできないため、どうにもならない。
（Windowsのanacondaプロンプトの場合にはdetectron2で（mac およびlinux環境でないため。）, Ubuntu on Windowsの場合には、torch==1.9.0+cu111のインストールで詰んでしまう...）
