## :computer: Get Started
#### Windows

Track-AnythingではNVIDIA製のGPU利用を前提としているが、私のパソコンにはNVIDIA製GPUが搭載されていない。（そのため、ローカル環境でapp.pyを実行すると、CUDAを認識できずエラーとなる。）
そのため、google colaboratory上でファイルを実行する。

#### 環境構築
新たにColab上でノートを作成し、ランタイムのタイプをGPUに変更する。その後本ディレクトリをアップロードする。
```
!git clone https://github.com/taktak/homeWork.git
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
