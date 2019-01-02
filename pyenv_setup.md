# pyenvを使用したPython環境の構築方法

ここでは、**pyenv**を使用してPythonの実行環境を構築する手順をまとめる。

## 周辺環境の構築

**pyenv**を導入する前に、Pythonのビルドに必要な周辺ライブラリ等をインストールする。

~~~bash
$ sudo apt install -y zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev libssl-dev libffi-dev python-tk
~~~

## pyenvの導入

**pyenv**はGitリポジトリをクローンすることで導入できる。

~~~bash
$ cd
$ git clone git://github.com/yyuu/pyenv.git .pyenv
~~~

**pyenv**の環境変数を`.bashrc`へ記述しておく。シェルから追加する方法は以下の通り。

~~~bash
$ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
$ echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
$ echo 'eval "$(pyenv init -)"' >> ~/.bashrc
$ exec $SHELL
~~~

最終的に、以下の内容が`.bashrc`に書かれていればよい。

~~~sh
# pyenv Configuration
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
~~~

ついでに、**pyenv**をアップデートする**pyenv-update**も合わせて導入しておく。

~~~bash
$ git clone git://github.com/yyuu/pyenv-update.git ~/.pyenv/plugins/pyenv-update
~~~

**pyenv**をアップデートする場合は、以下のようにシェルから入力するだけでよい。（**pyenv**導入直後は必要なし）

~~~bash
$ pyenv update
~~~

## Pythonのビルド

ここまで出来たら、`pyenv install`コマンドを使用してPythonをビルドする。

`pyenv install --list`でインストール可能なバージョンをチェックできるので、事前に確認しておくとよい。

~~~
$ pyenv install --list
~~~

インストール方法は、`pyenv install`に続けてバージョンを指定するだけでよい。

~~~bash
$ pyenv install 3.7.2
Downloading Python-3.7.2.tar.xz...
-> https://www.python.org/ftp/python/3.7.2/Python-3.7.2.tar.xz
Installing Python-3.7.2...
~~~

## Pythonのバージョン切り替え

前項の手順でビルドしたバージョンに切り替える場合は、`pyenv global`コマンドを使用する。

~~~bash
$ pyenv global 3.7.2
$ python --version
Python 3.7.2
~~~

## pipパッケージのインストール

まずは、pip本体を更新する。

~~~bash
$ pip install --upgrade pip
~~~

個々のpipパッケージをインストールする方法は以下の通り。

~~~bash
$ pip install <pipパッケージ名>
~~~

pipパッケージは必ずしもインストールする必要はない。自分用の備忘録として頻繁に使用するpipパッケージをまとめておく。

| No   | pipパッケージ名 |
| ---- | --------------- |
| 1    | ipython         |
| 2    | pylint          |
| 3    | pylama          |
| 4    | boto3           |
| 5    | flake8          |
| 6    | yapf            |
| 7    | numpy           |
| 8    | pandas          |
| 9    | matplotlib      |
| 10   | pillow          |
| 11   | scipy           |
| 12   | tensorflow      |
| 13   | keras           |
| 14   | chainer         |
| 15   | scikit-learn    |
| 16   | opencv-python   |

pipパッケージの更新は、**pip-review**を使用すると便利である。

~~~bash
$ pip install pip-review
$ pip-review --auto
~~~

