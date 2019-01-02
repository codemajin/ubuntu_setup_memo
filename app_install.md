# Ubuntu 18.04 インストール後の設定メモ

ここでは、**Ubuntu 18.04** インストール後に、主にシェル上から設定できる項目に焦点を当ててメモを残す。

## home直下のディレクトリ名を英語表記に戻す

~~~bash
$ env LANGUAGE=C LC_MESSAGES=C xdg-user-dirs-gtk-update
~~~

## Japanese Team Repositoryの追加と日本語パッケージのインストール

~~~bash
$ wget -q https://www.ubuntulinux.jp/ubuntu-ja-archive-keyring.gpg -O- | sudo apt-key add -
$ wget -q https://www.ubuntulinux.jp/ubuntu-jp-ppa-keyring.gpg -O- | sudo apt-key add -
$ sudo wget https://www.ubuntulinux.jp/sources.list.d/bionic.list -O /etc/apt/sources.list.d/ubuntu-ja.list
$ sudo apt update && sudo apt -y upgrade && sudo apt install -y ubuntu-defaults-ja
~~~

## リポジトリの追加

最新バージョンのアプリケーションを使用したい場合は、対象アプリケーションのリポジトリをPPAで管理する必要がある。

管理リポジトリは、以下のコマンドをシェルから入力することで追加できる。

~~~bash
$ sudo add-apt-repository -y -n <リポジトリ>
~~~

**Ubuntu 18.04** で管理できる主なリポジトリは以下のものがある。
([Sickly Life Blog](https://sicklylife.hatenablog.com/entry/2018/05/08/202315)を参考)

| No   | リポジトリ名                          | 関連アプリケーション                                         |
| ---- | ------------------------------------- | ------------------------------------------------------------ |
| 1    | ppa:sicklylife/ppa                    | aobook (青空文庫テキストビューアー)                          |
| 2    | ppa:graphics-drivers/ppa              | NVIDIA のビデオカード用ドライバー                            |
| 3    | ppa:sicklylife/mozc                   | Mozc                                                         |
| 4    | ppa:libreoffice/ppa                   | LibreOffice                                                  |
| 5    | ppa:sicklylife/libgweather-ja         | GNOME Weather (GNOME の天気アプリ)                           |
| 6    | ppa:rvm/smplayer                      | SMPlayer (動画プレイヤー)                                    |
| 7    | ppa:otto-kesselgulasch/gimp           | GIMP (画像編集アプリ)                                        |
| 8    | ppa:phoerious/keepassxc               | KeePassXC (パスワードマネージャー)                           |
| 9    | ppa:hluk/copyq                        | CopyQ (クリップボード履歴管理ツール)                         |
| 10   | ppa:webupd8team/y-ppa-manager         | Y PPA Manager (ppa 管理用 GUI アプリ)                        |
| 11   | ppa:sicklylife/gnucash                | GnuCash (財務管理アプリ)                                     |
| 12   | ppa:robert-tari/main                  | AACGain (aac ファイルの音量均一化ツール), Nero AAC (aac エンコーダー) |
| 13   | ppa:webupd8team/atom                  | Atom エディタ                                                |
| 14   | ppa:ubuntuhandbook1/audacity          | Audacity (サウンド編集アプリ)                                |
| 15   | ppa:ubuntuhandbook1/avidemux          | Avidemux (動画編集アプリ)                                    |
| 16   | ppa:yannubuntu/boot-repair            | Boot-Repair (ブートローダー修復アプリ)                       |
| 17   | ppa:ubuntuhandbook1/dvdstyler         | DVDStyler (DVD 作成アプリ)                                   |
| 18   | ppa:wereturtle/ppa                    | ghostwriter (Markdownエディタ)                               |
| 19   | ppa:danielrichter2007/grub-customizer | Grub Customizer (GRUB 編集アプリ)                            |
| 20   | ppa:stebbins/handbrake-releases       | HandBrake (動画変換ソフト)                                   |
| 21   | ppa:inkscape.dev/stable               | Inkscape (ベクトル画像編集アプリ)                            |
| 22   | ppa:ubuntuhandbook1/lives             | LiVES (ノンリニア動画編集アプリ)                             |
| 23   | ppa:flexiondotorg/audio               | MP3Gain (mp3 ファイルの音量均一化ツール)                     |
| 24   | ppa:ubuntuhandbook1/apps              | MuPDF (軽量な PDF ビューアー)                                |
| 25   | ppa:openshot.developers/ppa           | OpenShot (動画編集アプリ)                                    |
| 26   | ppa:peek-developers/stable            | Peek (デスクトップ録画 & gif アニメーション化アプリ)         |
| 27   | ppa:ubuntuhandbook1/pragha            | Pragha Music Player (軽量音楽プレイヤー )                    |
| 28   | ppa:transmissionbt/ppa                | Transmission (BitTorrent クライアント)                       |

## アプリケーションの追加

アプリケーションは、以下のコマンドをシェルから入力することで新規追加できる。

~~~bash
$ sudo apt install -y <アプリケーション名>
~~~

**Ubuntu 18.04** で仕様できる主なアプリケーションは以下の通りである（以下のブログを参考にまとめたものである）。

- [Ubuntu 18.04 LTSをインストールした直後に行う設定 & インストールするソフト](https://sicklylife.jp/ubuntu/1804/settings.html)
- [Sickly Life Blog](https://sicklylife.hatenablog.com/entry/2018/05/08/202315)

| No.  | アプリケーション名            | 説明                                                 |
| ---- | ----------------------------- | ---------------------------------------------------- |
| 1    | ubuntu-restricted-extras      | コーデック/フォントの追加拡張                        |
| 2    | gnome-tweaks                  | GNOMEデスクトップ向けの拡張                          |
| 3    | gnome-weather                 | GNOME Weather (GNOME の天気アプリ)                   |
| 4    | vlc                           | VLCメディアプレイヤー                                |
| 5    | mpv                           | mpv 動画プレイヤー                                   |
| 6    | gnome-mpv                     | mpv 動画プレイヤー (GTK+のフロントエンド用)          |
| 7    | smplayer                      | SMPlayer (動画プレイヤー)                            |
| 8    | audacious                     | Audacious (音楽プレイヤー)                           |
| 9    | easytag                       | EasyTAG(音楽ファイルのタグ編集ソフト)                |
| 10   | qtgain                        | QtGain (AAC Gain / MP3Gain の GUI)                   |
| 11   | viewnior                      | Viewnior (高速画像ビューアー)                        |
| 12   | nomacs                        | nomacs  (画像ビューアー)                             |
| 13   | gthumb                        | gThumb (GNOMEデスクトップ環境向け画像ビューアー)     |
| 14   | gimp                          | GIMP (画像編集アプリ)                                |
| 15   | nautilus-image-converter      | 画像を右クリックからリサイズ/回転するツール          |
| 16   | atril                         | PDFビューアー                                        |
| 17   | qpdfview                      | タブ型PDFビューアー                                  |
| 18   | geany                         | コード補完機能付きエディタ                           |
| 19   | geany-plugins                 | geanyのプラグイン                                    |
| 20   | meld                          | 差分ビューアー                                       |
| 21   | fslint                        | ファイル整理ソフト                                   |
| 22   | bleachbit                     | 不要ファイル削除ツール                               |
| 23   | doublecmd-gtk                 | マルチプラットフォーム対応の二画面タブ型ファイラー   |
| 24   | keepassxc                     | パスワード管理ソフト                                 |
| 25   | gsmartcontrol                 | HDDやSSDのS.M.A.R.T.をチェックするためのツール       |
| 26   | gnome-shell-extensions-gpaste | GPaste (GNOME 用のクリップボード拡張アプリ)          |
| 27   | copyq                         | CopyQ (クリップボード履歴管理ツール)                 |
| 28   | synaptic                      | aptのフロントエンド                                  |
| 29   | y-ppa-manager                 | ppa管理ソフト                                        |
| 30   | ppa-purge                     | 追加したppaを削除し、バージョンを元に戻すツール      |
| 31   | gftp                          | FTPクライアント                                      |
| 32   | filezilla                     | FTP/FTPS/SFTPクライアント                            |
| 33   | gnucash                       | GnuCash (財務管理アプリ)                             |
| 34   | xfsprogs                      | XFS ファイルシステム管理用ユーティリティ             |
| 35   | build-essential               | コンパイラ、ライブラリなど                           |
| 36   | libgtk-3-dev                  | GTK3 ライブラリ                                      |
| 37   | emacs                         | emacs エディタ                                       |
| 38   | aacgain                       | AACGain (aac ファイルの音量均一化ツール)             |
| 39   | aobook                        | aobook (青空文庫テキストビューアー)                  |
| 40   | atom                          | ATOM (テキストエディター)                            |
| 41   | audacity                      | Audacity (サウンド編集アプリ)                        |
| 42   | avidemux2.6-qt                | Avidemux (動画編集アプリ)                            |
| 43   | boot-repair                   | Boot-Repair (ブートローダー修復アプリ)               |
| 44   | dvdstyler                     | DVDStyler (DVD 作成アプリ)                           |
| 45   | ghostwriter                   | ghostwriter (マークダウンエディター)                 |
| 46   | gnome-clocks                  | GNOME Clocks (GNOME の時計アプリ)                    |
| 47   | grub-customizer               | Grub Customizer (GRUB 編集アプリ)                    |
| 48   | gshutdown                     | GShutdown (シャットダウンタイマー)                   |
| 49   | gufw                          | gufw (ファイアーウォールの GUI)                      |
| 50   | handbrake                     | HandBrake (動画変換ソフト)                           |
| 51   | inkscape                      | Inkscape (ベクトル画像編集アプリ)                    |
| 52   | lives                         | LiVES (ノンリニア動画編集アプリ)                     |
| 53   | mp3gain                       | MP3Gain (mp3 ファイルの音量均一化ツール)             |
| 54   | mupdf                         | MuPDF (軽量な PDF ビューアー)                        |
| 55   | neroaac                       | Nero AAC (aac エンコーダー)                          |
| 56   | openshot-qt                   | OpenShot (動画編集アプリ)                            |
| 57   | peek                          | Peek (デスクトップ録画 & gif アニメーション化アプリ) |
| 58   | pragha                        | Pragha Music Player (軽量音楽プレイヤー )            |
| 59   | qshutdown                     | Qshutdown (シャットダウンタイマー)                   |
| 60   | qwinff                        | QWinFF (動画変換アプリ)                              |
| 61   | transmission-gtk              | Transmission (BitTorrent クライアント)               |
| 62   | ubuntu-cleaner                | Ubuntu Cleaner (クリーナーアプリ)                    |
| 63   | ukuu                          | ukuu (Ubuntu Kernel Update Utility)                  |

## フォントの追加

フォントも、以下の通り`apt install`で追加できる。

~~~bash
$ sudo apt install <フォント名>
~~~

**Ubuntu 18.04** で使用できるフォントの一例を以下にまとめる。

| No   | フォント名              | 説明                   |
| ---- | ----------------------- | ---------------------- |
| 1    | fonts-mplus             | M+                     |
| 2    | fonts-migmix            | MigMix                 |
| 3    | fonts-mmcedar           | MMCedar                |
| 4    | fonts-umeplus           | UmePlus                |
| 5    | fonts-horai-umefont     | 梅フォント             |
| 6    | fonts-motoya-l-maruberi | モトヤLマルベリ3等幅   |
| 7    | fonts-motoya-l-cedar    | トヤLシーダ3等幅       |
| 8    | fonts-ipafont-gothic    | IPAフォント (ゴシック) |
| 9    | fonts-ipafont-mincho    | IPAフォント (明朝)     |

## Oracle Java のインストール

Java 10 をインストール場合は、以下のコマンドをシェルから入力する。

~~~bash
$ sudo add-apt-repository -y -n ppa:linuxuprising/java
$ sudo apt update
$ sudo apt install oracle-java10-installer
~~~

Java 8 の場合は、以下の通り。

~~~bash
$ sudo add-apt-repository -y -n ppa:webupd8team/java
$ sudo apt update
$ sudo apt install oracle-java8-installer
~~~

## Visual Studio Code のインストール

VSCodeは、[Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux)を参考にしてインストールする。

~~~bash
$ curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
$ sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
$ sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
$ sudo apt update && sudo apt install -y code
~~~

# i386 Architecureの追加

64ビットOS上で32ビット用の実行ファイルを作成するために、ライブラリを追加でインストールしておく。

~~~bash
$ sudo dpkg --add-architecture i386
$ sudo apt update
$ sudo apt install libc6:i386 libncurses5:i386 libstdc++6:i386 gcc-multilib g++-multilib
~~~

その他、[Code Composer Studio](http://www.tij.co.jp/tool/jp/CCSTUDIO)を使用する場合は、以下のライブラリを追加でインストールしておく。

~~~bash
$ sudo apt install libc6:i386 libx11-6:i386 libasound2:i386 libatk1.0-0:i386 libcairo2:i386 libcups2:i386 libdbus-glib-1-2:i386 libgconf-2-4:i386 libgcrypt20:i386 libgdk-pixbuf2.0-0:i386 libgtk-3-0:i386 libice6:i386 libncurses5:i386 libsm6:i386 liborbit2:i386 libudev1:i386 libusb-0.1-4:i386 libstdc++6:i386 libxt6:i386 libxtst6:i386 libgnomeui-0:i386 libusb-1.0-0-dev:i386 libcanberra-gtk-module:i386 gtk2-engines-murrine:i386 unzip
~~~

## その他

開発関連用として、以下のツールをインストールしておいてもよい。

| No   | ツール                | 説明       |
| ---- | --------------------- | ---------- |
| 1    | graphviz              | Graphviz   |
| 2    | cppcheck              | CppCheck   |
| 3    | googletest            | GoogleTest |
| 4    | cpputest              | CppUTest   |
| 5    | doxygen               | Doxygen    |
| 6    | cmake                 | Cmake      |
| 7    | gcc-arm-linux-gnueabi | ARM用GCC   |
| 8    | qemu-user-static      | QEMU       |
