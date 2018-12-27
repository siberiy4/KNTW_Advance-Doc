# 事前配布資料  

今回のワークショップで使いそうなワードを載せてみました。

## ネットワークの用語  
### LAN とは
同じ建物の中や、一つの家庭などの限定された範囲で接続できるネットワークのこと。
  
### WAN とは  
遠く離れた場所と場所がつながったネットワーク。
簡単に言えば、LANとLANをつなぐ。
  
## ネットワークを構成するもの

- ルータや、L2ハブ、サーバなどの機器
- UTPケーブルや光ファイバなどのケーブル

#### 機器
今回使う機材にはGigabit Ethernet(GiGと書かれたものなど)のポートと Fast Ethernet(FEと書かれたものなど)のポートが存在する。  
Fastは上限が100Mbps、Gigabitは上限が1Gbpsで通信する。

- スイッチングハブ
    MACアドレスを見てパケットを流してくれる

<img src="computer_hub_loop_setsuzoku.png" width=20%>

- ルータ  
    ネットワークの中継器。IPを見てパケットを流すなど、ルーティングプロトコルが扱える。

<img src="computer_wireless.png" width=20%>



#### ケーブル
- 遠距離通信を支える光ファイバ。  
    高速通信を遠くまで敷設できる代わりに壊れやすい。  
  
- 近場のお供、UTPケーブル  
    通信の距離減衰が激しいが曲げたりできる。  
    　クロスケーブル：同種の危機(ルータとルータなど)の接続に使う  
    　ストレートケーブル：多種(ルータとPCなど)の接続に使う  
    しかし近年はautoMDI/MDI-Xがあるため、意識せずとも使うことができる  

### Ciscoルータの基本コマンド
今回のワークショップで直接触れるネットワーク機器は、CISCOのルータです。
CISCO機器はCLIで操作するため、基本的なコマンドを紹介しておきたいと思います。
コマンドの入力はtabで補完することができます。
```
conf
```
でtabをうつと
```
configure
```
まで保管してくれます。(ただし、入力しているときの文字でコマンドが特定できるときのみです)

また、`?`は入力可能なコマンドを表示してくれます。
```
interface GigabitEthernet ?
```
でエンターを押すとその下に
```
<0~8>
```
のように表示してくれます。(今回は選択可能なインターフェースが表示されています)
`?`は単語の途中でも入力することができるので、
```
int?
```
のように使うこともできます。

#### モード
CISCO のIOSではユーザーモードと特権モードの2つのアクセスレベルが存在する。  
<img src="image.png" width=70%>

Linuxの管理者と一般ユーザのようなもの。  
ユーザモードではコマンドが制限されている(設定の一部が確認できる程度)が、特権になるとすべてのコマンドが入力できる。  
ユーザモードでは` > `が表示されているときはユーザモード、` # `が表示されているときは特権モードである。  
ユーザモードから特権モードになるためには
```
enable 
```
と入力することで入ることができる。  
  
この状態ではその機器のすべての設定を確認できる。
この状態から  
  
```
configure terminal
```

と入力することで、`グローバルコンフィギュレーションモード`になり設定を打ち込むことができる。
  
運用する際は、ユーザモードから特権に変わる時(`enable`をうった時)にパスワードを要求する設定になっている場合が多い。

#### show
設定を確認するコマンド。

```

```



#### interface


### ネットワークの技術
  
#### DHCP
IPアドレスを自動的に割り当てたり、デフォルトゲートウェイ、使用するDNSなどの情報を伝えるプロトコル。  
スマホやPCをWiFiに接続するとすぐにネットが使えるのはDHCPを自動で受け取るようにデフォルトで設定されているためである。
CISCO機器では、DHCPをはくことのできるDHCPサーバになることも、インターフェースごとに設定すればDHCOを受け取るDHCPクライアントになることもできる。
GigabitEthernet 0でクライアントとしてDHCPを受け取り、GigabitEthernet 1でサーバとしてDHCP配ることもできます。

#### NAT

#### ACL


#### VLAN


#### ルーティング
- IGP(説明)
    - RIP / RIP version2
  
    - OSPF

- EGP(説明)
    - BGP