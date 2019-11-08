# CentOS6-Minimalのインストール
 - Minimal64bit版を入手
 - VMwareのインストール
 - ネットワークを共有する 
## 起動前
 - 読み込みCDの部分の一つ目がautosetuoだったか何かになってるのでDLしたisoファイルにしておく。二つ目もそうしておく。
 - 起動するとインストール画面に行くのでインストールする。

## 起動後
 - インストール後、ログインする。CUIのみで操作することになる。
 - 重要なのは``/etc/sysconfig/network-scripts/ifcfg-eth0``
 - こいつを編集する。

```
DEVICE=eth0
BOOTPROTO=none
ONBOOT=yes
NETMASK=255.255.255.0
IPADDR=192.168.10.31
USERCTL=no
NM_CONTROLLED=no
```
 - こんな感じになってるので``onboot=yes``,``NM_CONTROLLED=no``にしてescし、`:wq`で書き込み保存。保存しないなら``:q!``
 - ``system network restart``とし、pingなどができれば成功!