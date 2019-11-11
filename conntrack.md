# Conntrackのインストール(CentOS6)
- ~~wgetをインストールしておく~~

~~```~~
wget http://sourceforge.net/projects/flexbox/files/flexbox-release-1-1.noarch.rpm
rpm -ivh flexbox-release-1-1.noarch.rpm
yum -y install conntrack-tools
~~```~~

~~終わり~~

## EPELリポジトリの利用
 - リポジトリ:データの一時的保管庫。
 - 公式:ttps://fedoraproject.org/wiki/EPEL/ja

 - EPELにconntrackがあることは``ttps://centos.pkgs.org/6/epel-x86_64/conntrack-tools-0.9.13-3.el6.x86_64.rpm.html``からわかる。
 - 公式に書いてあるように``yum install epel-release をだけ実行したら、EPEL
  を使用できます.``

 - インストールした後、初期設定では自動でEPELリポジトリから色々とインストールできるようになっているが、CentOSではサポートされていないため、利用は自己責任となる。
 - 利用が自己責任なのに初期設定で自動利用になってしまっているので設定を変更する。

### EPELリポジトリ利用設定の変更
 - ``/etc/yum.repos.d/epel.repo``
 - これがリポジトリ利用設定ファイルなのでviで編集する。

```repo
[epel]
name=Extra Packages for Enterprise Linux 7 - $basearch
#baseurl=http://download.fedoraproject.org/pub/epel/7/$basearch
mirrorlist=https://mirrors.fedoraproject.org/metalink?repo=epel-7&arch=$basearch
failovermethod=priority
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
```

 - ここの``enabled=1``を0に変更して保存して編集終了。

### EPELリポジトリを利用してソフトインストール
 - yumコマンドに``--enablerepo=epel``を追加する。

 - 本来の目的であるconntrackをインストールする。
 -  ``yum --enablerepo=epel -y install conntrack``

終わり！

###参考
 - ttps://www.server-memo.net/centos-settings/centos7/add-repo.html



