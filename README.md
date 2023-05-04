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
```
!git clone https://github.com/showlab/VLog.git
%cd VLog
%mkdir checkpoints
%cd checkpoints
!wget "https://datarelease.blob.core.windows.net/grit/models/gr
%cd ..
```



VLogはCPUで実行できるため、これ以降はローカル環境で実行する。（Ubuntu18.04.5 on Windows環境で実行した）
```
git clone https://github.com/showlab/VLog.git
```
でVLogディレクトリをクローンしたのち、
```
cd VLog
mkdir checkpoints
wget -c https://datarelease.blob.core.windows.net/grit/models/grit_b_densecap_objectdet.pth
cd ..
```
その後、
```
conda create -n -y vlog python=3.8
conda activate vlog
```
としたのち、pytorchのver1系統をインストールします。（公式サイトを参照しながらインストールしてください。）
```
conda install pytorch==1.13.1 torchvision==0.14.1 torchaudio==0.13.1 cpuonly -c pytorch
```
その後、
```
pip install -r requirements.txt
```
を実行します。
