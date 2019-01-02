# rbenvを使用したRuby環境の構築方法

ここでは、**rbenv**を使用してRubyの実行環境を構築する手順をまとめる。

## 周辺環境の構築

**rbenv**を導入する前に、Rubyのビルドに必要な周辺ライブラリ等をインストールする。

~~~bash
$ sudo apt -y install git curl g++ make
$ sudo apt -y install zlib1g-dev libssl-dev libreadline-dev
$ sudo apt -y install libyaml-dev libxml2-dev libxslt-dev
$ sudo apt -y install sqlite3 libsqlite3-dev nodejs
~~~

## rbenvの導入

**rbenv**はGitリポジトリをクローンすることで導入できる。

~~~bash
$ cd
$ git clone git://github.com/sstephenson/rbenv.git .rbenv
~~~

**rbenv**の環境変数を`.bashrc`へ記述しておく。シェルから追加する方法は以下の通り。

~~~bash
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc
$ exec $SHELL
~~~

最終的に、以下の内容が`.bashrc`に書かれていればよい。

~~~sh
# rbenv Configuration
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
~~~

ここまで出来たら、Rubyをビルドするためのツール**ruby-build**もGitHubからクローンしておく。

~~~bash
$ mkdir -p ~/.rbenv/plugins
$ cd ~/.rbenv/plugins
$ git clone git://github.com/sstephenson/ruby-build.git
~~~

ついでに、**rbenv**をアップデートする**rbenv-update**も合わせて導入しておく。

~~~bash
$ cd
$ git clone https://github.com/rkh/rbenv-update.git ~/.rbenv/plugins/rbenv-update
~~~

**rbenv**をアップデートする場合は、以下のようにシェルから入力するだけでよい。（**rbenv**導入直後は必要なし）

~~~bash
$ rbenv update
~~~

## Rubyのビルド

ここまで出来たら、`rbenv install`コマンドを使用してRubyをビルドする。

`rbenv install --list`でインストール可能なバージョンをチェックできるので、事前に確認しておくとよい。

~~~
$ rbenv install --list
~~~

インストール方法は、`rbenv install`に続けてバージョンを指定するだけでよい。

~~~bash
$ rbenv install 2.6.0
Downloading ruby-2.6.0.tar.bz2...
-> https://cache.ruby-lang.org/pub/ruby/2.6/ruby-2.6.0.tar.bz2
Installing ruby-2.6.0...
~~~

## Rubyのバージョン切り替え

前項の手順でビルドしたバージョンに切り替える場合は、`rbenv global`コマンドを使用する。

~~~bash
$ rbenv global 2.6.0
$ ruby -v
ruby 2.6.0p0 (2018-12-25 revision 66547) [x86_64-linux]
~~~

## gemパッケージの更新

ついでに、gemパッケージも更新しておくとよい。

まずは、`.gemrc`を作成する。

~~~bash
$ touch ~/.gemrc
$ echo 'install: --no-document' >> ~/.gemrc
$ echo 'update: --no-document' >> ~/.gemrc
~~~

gem本体を更新する。

~~~bash
$ gem update --system
~~~

続いて、gemパッケージを更新する。

~~~bash
$ gem update
~~~

## gemパッケージのインストール

ここの内容は、別にやらなくてもいい。自分用の備忘録として頻繁に使用するgemパッケージをまとめておく。

gemパッケージは、以下のように行う。

~~~bash
$ gem install <gemパケージ名>
~~~

| No   | gemパッケージ名     | 補足                                   |
| ---- | ------------------- | -------------------------------------- |
| 1    | bundle              | -                                      |
| 2    | bundler             | -                                      |
| 3    | pry                 | -                                      |
| 4    | rsense              | -                                      |
| 5    | byebug              | -                                      |
| 6    | asciidoctor         | -                                      |
| 7    | asciidoctor-diagram | -                                      |
| 8    | coderay             | -                                      |
| 9    | asciidoctor-pdf     | --pre オプション付きでインストールする |
| 10   | asciidoctor-pdf-cjk | -                                      |
| 11   | ruby-debug-ide      | -                                      |
| 12   | debase              | -                                      |
| 13   | reek                | -                                      |
| 14   | rubocop             | -                                      |
| 15   | fasterer            | -                                      |
| 16   | debride             | -                                      |
| 17   | ruby-lint           | -                                      |
| 18   | rcodetools          | -                                      |
| 19   | fastri              | -                                      |
| 20   | solargraph          | -                                      |