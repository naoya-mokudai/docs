Ansibleを使ってPersoniumを始めよう。
------------------------------------

概要
----

本書ではansibleを使用してPersoniumの環境を構築する方法について説明します。  
ansibleに興味のあるかたは以下のページもあわせてご参照ください。  
[HOW ANSIBLE WORKS](http://www.ansible.com/how-ansible-works)

### Personiumのユニット構成

Personiumのユニットは評価、開発、確認、運用等々の様々な異なる目的に応じて構成することが可能です。Personiumは必要に応じて簡単に、自動的に環境を構築できるセットアップツールを提供しています。  
Personiumのユニットはセットアップツールを使用せずに構築することも可能ですが、Personiumのユニットを簡単に構築するためにセットアップツールの使用をお勧めいたします。

### Personiumにおける各サーバーの役割

Personiumのユニットは以下の役割を持ったサーバーから構成されます。これらの役割は相互に接続された単独または複数のサーバーに割り当てることが可能です。

|役割|必須|詳細|
|:--|:--|:--|
|Web|必須|リバースプロキシーサーバー。インターネットからのアクセスが可能なグローバルなIPアドレスを保有する必要があります。<br>|
|AP|必須|Personiumが動作するアプリケーションサーバーです。<br>|
|ES|必須|ElasticSearchが動作するサーバーです。<br>|
|MQ|必須|ActiveMQが動作するサーバーです。<br>|
|NFS|必須<br>|ネットワークファイルシステム(NFS)が動作するサーバーです。<br>|
|Bastion|オプション|踏み台サーバ。各サーバへのsshでのアクセスを中継させるためにのサーバです。<br>|

### Personiumセットアップツール

本セットアップツールはPersoniumをインストールする前に、あなたのサーバー（linuxのサーバーまたはWindowsやMac上の仮想マシン）へのミドルウェアの導入やOSやネットワークの設定を行います。  
セットアップツールにはPersoniumとのユニットの構成に応じて複数の形式がありますので、あなたの目的に応じたセットアップツールをご使用ください。

#### パターン1 : 1 Server

-   機器環境 : **Linux**
-   Personiumユニット構成サーバー台数 : **1 Server**
-   サーバー1の構成 : Web, AP, ES, MQ, NFS
-   構築時間: 1 時間
-   使用するセットアップツール: [ansible/1-server\_unit](https://github.com/personium/ansible/tree/master/1-server_unit "1-server_unit")
-   注意  
    もしもあなたが、Personiumにより一層興味を持ち、アプリケーションの開発やテストを実施してみたいと思ったならば、本構成を使用することができます。あなたは1台構成のPersonium環境を入手することができます。

\* Vagrant を利用して簡単にローカルマシン環境に仮想マシンを構築し、Personium の動作を確認することが可能です。設定方法については[setup-vagrant](https://github.com/personium/setup-vagrant)を参照してください。

#### パターン2 : 3 Servers

-   機器環境 : **Linux**
-   Personiumユニット構成サーバー台数 : **3 Servers**
-   サーバー1の構成 : Bastion, Web
-   サーバー2の構成 : AP, MQ, NFS
-   サーバー3の構成 : ES
-   構築時間 : 2 時間
-   使用するセットアップツール: [ansible/3-server\_unit](https://github.com/personium/ansible/tree/master/3-server_unit "3-server_unit")
-   注意  
    　もしもあなたがPersoniumプロジェクトにご参加いただき、いくつかの素晴らしいアプリケーションをリリースしようとするならば、3台のサーバからユニットが構成される、本構成をお勧めします。

本ドキュメントでは、Personiumを構成する基本的なパターンをご紹介しています。  
目的に応じて最適なパターンをご選択ください。
