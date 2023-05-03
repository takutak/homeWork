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

#### VLogの実行
ここからは、ダウンロードしたmp4ファイルに対してVLogアプリケーションを適用することを考えます。
まず、google colabratoryにおけるpytorchのバージョンについて確認します。まずパッケージをインストールします。
```
!git clone https://github.com/showlab/VLog.git
```
```
%cd VLog
%mkdir checkpoints
%cd checkpoints
!wget -c https://datarelease.blob.core.windows.net/grit/models/grit_b_densecap_objectdet.pth
%cd ..
```
#### Pytorchのバージョン確認と変更について（ver1.9に設定している方は読み飛ばしていただいて結構です。)
多くの人は、Google ColabのPytorchのバージョンは最新の2.0以降のものになっているかと思います。しかしVLogは1.9系統でなければエラーを吐き出すため、以下の手順でpytorchのver.1系統を再度インストールする必要があります。（Condaを使った仮想環境をcolab上に構築します。）
```
!wget -c https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
!chmod +x Miniconda3-latest-Linux-x86_64.sh
!bash ./Miniconda3-latest-Linux-x86_64.sh -b -f -p /usr/local
```
を実行し、colab上でminicondaをインストールする。その後、
```
!conda create -n vlog python=3.8
```
```
%cd VLog
