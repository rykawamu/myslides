## WEBエンジニアなら知っている
## CUIクイズ

#### WEBエンジニア勉強会 #10前座LT
#### 2018.11.09 : MzRyuKa

---

## 自己紹介

* みずりゅ
* Twitter: <font color=gold>@MzRyuKa</font>
* 好きなもの：ネコ、うさまる、技術な話全般
* 最近触っている言語：golang、Elixir、Vue.js
* アイコンはTwitterでは<font color=gold>画像のネコ</font>、connpassでは「<font color=gold>うさまる</font>」です。

<img src="nuko.png" style="width:25%;"/>

---

## 今回の趣旨

* 今は簡単に開発環境を整えられる時代です。

* しかし、どんなに便利になっても<font color=gold>問題発生時に最後に触るのはコンソール</font>、そう<font color=gold>CUI</font>なのです。
* CUI:（character user interface または console user interface）

---

## 今回の趣旨(続き)

* これから<font color=gold>WEBと関連するCUI</font>に関する２ー３択のクイズをお出しします。

* 乾杯が待ち遠しい皆さんの時間つぶしにしてください。

* もし知らない内容があったのなら活用してみてください。

---

## 練習問題

* SELinuxで<font color=gold>一時的にアクセス制限を解除</font>したい。以下のコマンドを実施後、<font color=gold>SELinuxはどのモード</font>になっているか？

```
# setenforce 0
```

* A：Disabled
* B：Permissive
* C：Enforcing

--

#### 回答

* <b>B：Permissive</b>

--

#### 解説

* setenforceコマンドで「0」を指定すると、「<font color=gold>SELinuxは有効だが、アクセス制限は行わず警告を出力</font>」のモードである「Permissive」となります。
* なお、「1」を指定した場合は、アクセス制限が発生する「Enforcing」となります。それ以外の数値は無効です。

---

と、こんな感じで進めます。

回答は心の中で。

---

## 第一問

* サービス問題。<font color=gold>Solaris 10</font>で、apacheをOS起動時に<font color=gold>自動起動するスクリプトファイル</font>はどれか。

```
A：/etc/rc3.d/D50apache
```
```
B：/etc/rc3.d/K50apache
```
```
C：/etc/rc3.d/S50apache
```

--

#### 回答

* <b>C：/etc/rc3.d/S50apache</b>

--

#### 解説

* Solaris10では、「/etc/rcX.d」(Xは任意の数字)の下にあるスクリプト名が「<font color=gold>S</font>」で始まるファイル名の場合、自動起動します。
* 一方、「K」で始まる場合は、OS停止時の自動停止用スクリプトになります。それ以外で始まる場合は特に意味は持ちません。

---

## 第二問

* 「<font color=gold>マンガでわかるDocker2</font>」よりコマンド借用。空欄[ ]に入る設定値はどれか答えよ。
* 内容は「<font color=gold>ホストのカレントディレクトリをコンテナ内の所定のパスにマウントする</font>」である。

```
$ docker run -d -p 80:80 --name myapp [ ] php:7.0-apache
```

* A： -v $(pwd):/var/www/html
* B： -v /var/www/html:$(pwd)
* C： -v /var/www/html

--

#### 回答

* <b>A：-v $(pwd):/var/www/html</b>

--

#### 解説

* ボリュームのマウントは、「-v」オプションの後に、<font color=gold><ホスト側のディレクトリ>:<コンテナ側のディレクトリ></font>の順で指定します。
* B：の場合は、ホストとコンテナの順が入れ替わっています。また、動作するかも不明ですし、動作しても実施内容とは異なります。
* C：の場合は、ホスト上の所定の位置にディレクトリを作って、コンテナ側のディレクトリにマウントします。

---

## 第三問

* Gitで「履歴をコミット毎に<font color=gold>１行</font>で表示し、各コミットで変更された<font color=gold>ファイルのリスト</font>を表示する。」コマンドはどれか。

```
A：git log --oneline
```
```
B：git log --oneline --shortstat
```
```
C：git log --oneline --stat
```

--

#### 回答

* <b>C：git log --oneline --stat</b>

--

#### 解説

* 「--oneline」は<font color=gold>履歴をコミット毎に１行</font>で表示するオプション。
* 「--stat」は各コミットで変更された<font color=gold>ファイルのリスト</font>を表示するオプション。
* 各コミットで変更されたファイルのリストを一行で表示する場合、オプションには「--shortstat」を使用する。

---

## 第四問

* サーバが<font color=gold>firewalld</font>でアクセス制限をかけている。ここで、特定のIPアドレス（192.168.1.0/24）に対してhttpsを<font color=gold>３日間だけ拒否</font>したい。<font color=gold>有効な設定</font>すべてを選べ。

```
A：firewall-cmd --remove-rich-rule="rule family=ipv4 source
    address=192.168.1.0/24 service name=https accept" --timeout=72h
```

```
B：firewall-cmd --permanent --add-rich-rule="rule family=ipv4 source
    address=192.168.1.0/24 service name=https drop" --timeout=72h
```

```
C：firewall-cmd --add-rich-rule="rule family=ipv4 source
    address=192.168.1.0/24 service name=https drop" --timeout=3d
```

--

#### 回答

* <b>なし</b>

--

#### 解説

* 時間指定「<font color=gold>--timeout</font>」は「<font color=gold>--add-rich-rule</font>」のみ利用可能です。許可(accept)、拒否（drop）の両方で利用できます。「--remove-rich-rule」には使えません。
* 永続設定「<font color=gold>--permanent</font>」と併用できません。
* 「--timeout」で指定可能な単位は「<font color=gold>s</font>」「<font color=gold>m</font>」「<font color=gold>h</font>」のみです。それ以外の文字はエラーです。
* 設定するとしたら以下のイメージ。

```
firewall-cmd --add-rich-rule="rule family=ipv4 source
    address=192.168.1.0/24 service name=https drop" --timeout=72h
```


---

## 第五問

* <font color=gold>ダイジェスト認証</font>が設定されているページに対して<font color=gold>curl</font>でアクセスする場合、有効なコマンドを全て選択せよ。
* ユーザ／パスワードはuser1とpass1とする。

```
A：curl --user “user1:pass1” https://example.com/foo/bar.json
```
```
B：curl --basic -u “user1:pass1” https://example.com/foo/bar.json
```
```
C：curl --digest -u “user1:pass1” https://example.com/foo/bar.json  
```

--

#### 回答

* <b>C：curl --digest -u “user1:pass1” https://example.com/foo/bar.json のみ</b>

--

#### 解説

* 「<font color=gold>--digest</font>」を利用してダイジェスト認証を行います。なお、Basic認証の場合では「A」と「B」のどちらでも可です。
* 認証に利用するオプション「-u」と「--user」は同じ意味です。
* 余談：Basic認証とダイジェスト認証の大きな違いは変換方法です。Basic認証はBase64で、ダイジェスト認証はMD5で、変換されます。

--

* 余談２：認証に失敗すると<font color=gold>ステータス401</font>が返されます。「<font color=gold>部外者め</font>」ってことですね。

---

## 第六問

* curlでWebサイトにログインして<font color=gold>cookie情報を保存</font>する時に利用するコマンドはどれか？
* 「cookie.txt」がcookie情報を保存したファイルとする。

```
A：curl -a cookie.txt -d “user=user1” -d “pass=pass1”
　　　　 https://example.com/login
```
```
B：curl -b cookie.txt -d “user=user1” -d “pass=pass1”
　　　　 https://example.com/login
```
```
C：curl -c cookie.txt -d “user=user1” -d “pass=pass1”
　　　　 https://example.com/login
```

--

#### 回答

* <b> C：curl -c cookie.txt -d “user=user1” -d “pass=pass1” https://example.com/login</b>

--

#### 解説

* <font color=gold>cookie情報を保存</font>する場合、「<font color=gold>-c <ファイル名></font>」を利用します。
* 「<font color=gold>-b <ファイル名></font>」は、cookie情報を利用してURLにアクセスする際に利用します。
* 「-a」はcookie情報に関係しません。
* 「-d “id値＝値”」はformの値を送信する際に利用します。上記の例ではログイン時に利用するユーザとパスワードを指定して送信しています。


---

## 第七問

* コンソールでcsvファイルをダウンロードする。しかし、別のページに<font color=gold>リダイレクト</font>される可能性がある。どちらのコマンドを選択するか？

* A：wget  https://example.com/foo/bar.csv
* B：curl  https://example.com/foo/bar.csv

--

#### 回答

* <b>A：wget  https://example.com/foo/bar.csv</b>

--

#### 解説

* wgetもcurlもWebサイトのデータ（htmlや任意のファイルなど）にアクセスしてその情報を取得できます。
* wgetの特徴としては、デフォルトで「<font color=gold>再帰的</font>」にダウンロードしてくれます。
* 一方、curlの場合にはデフォルトではリダイレクト先を辿ってくれません。ただし、オプションとして「-L」を付与することで、リダイレクト先を追ってくれます。

---

## 第八問

* wgetコマンドを使って、<font color=gold>ダウンロードしたファイルの名前</font>を変更したい。どちらのオプションを指定する？

* A：wget -O hoge.csv https://example.com/foo/bar.csv
* B：wget -o hoge.csv  https://example.com/foo/bar.csv

--

#### 回答

* <b>A：wget -O hoge.csv https://example.com/foo/bar.csv</b>

--

#### 解説

* wgetで取得した<font color=gold>ファイルを任意の名前で保存したい場合、「-O」(大文字のオー)</font>をオプションに指定した後でファイル名を指定します。
* 「-o」(小文字のオー)を指定した場合には、wgetでは処理経緯の情報が、指定したファイル名に格納されます。
* ちなみに、curlでファイル名を保存する際には「-o」を指定するので混乱しがちです。


---

## 第九問

* Apache HTTP Serverの2.2系。あるディレクトリ配下はIPアドレスで制限されている。ここへ別のIPアドレスの設定を追加した。

```
Allow from 192.168.0.0/16 #内部からアクセス許可 
```

* その後で実行するコマンドはどれか。

```
A：apachectl configtest 
```
```
B：apachectl configcheck
```
```
C：apachectl restart
```

--

#### 回答

* <b>A：apachectl  configtest</b>

--

#### 解説

* このコマンドを実行すればapacheの設定ファイルの内容が正しいか<font color=gold>書式チェック</font>します。
* 設定変更後に実行して<font color=gold>syntax error</font>がでないことを確認しましょう。
* 「configcheck」は存在しません。

--

#### 余談

* 設定ファイル中でコメント行を示す<font color=gold>「#」は行の先頭以外に置くとsyntax error</font>となります。
* 特定のOSとapacheのバージョンでは、<font color=gold>アクセス制限が無効になりどこからもアクセス可</font>となるバグもありました。（cve-2017-12171）

---

## 第十問

* CentOS 7系でapacheをyumでインストールした。以下のコマンドと同じ操作はどれか？
*  挙動としては「<font color=gold>緩やかな再起動</font>」が行われる。

```
# systemctl  reload  httpd
```

* A：httpd -k condrestart 
* B：httpd -k reload
* C：httpd -k graceful

--

#### 回答

* <b>C：httpd -k graceful</b>

--

#### 解説

* 「緩やかな再起動」といえば「<font color=gold>graceful</font>」です。<font color=gold>WEBサービスが停止せず、かつ実行中のリクエストを中止せず</font>に、設定情報を読み直して反映させます。（できない設定もある）
* なお、reloadは「実行中のリクエストは中止」されます。WEBサービスは停止されません。
* 「condrestart」とは「conditional  restart」の意味です。起動済みなら停止後に起動しますが、停止済みの場合は起動しません。


---

To be continued ...
