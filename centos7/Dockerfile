FROM centos:centos7

# CentOS ProjectのGPG公開鍵をインストールする
RUN rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

# インストール済みのパッケージをアップデート＆キャッシュのクリア
RUN yum -y update && yum clean all

# 言語を日本語に設定
RUN localedef -i ja_JP -f UTF-8 ja_JP.UTF-8
RUN echo 'LANG="ja_JP.UTF-8"' >  /etc/locale.conf
ENV LANG ja_JP.UTF-8

# 日付を日本語に設定
RUN echo 'ZONE="Asia/Tokyo"' > /etc/sysconfig/clock
RUN rm -f /etc/localtime
RUN ln -fs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# manをインストールする前に、manファイルをインストールするように設定変更
RUN sed -i -e"s/^tsflags=nodocs/\# tsflags=nodocs/" /etc/yum.conf

# manと、man-pagesをインストール
RUN yum -y install man
RUN yum -y install man-pages.noarch
RUN yum -y install man-pages-ja.noarch

#ネットワーク関連をインストール
RUN yum -y install NetworkManager
RUN yum -y install net-tools
RUN yum -y install iproute
RUN yum -y install nmap
RUN yum -y install sudo
RUN yum -y install less
RUN yum -y install bind-utils
RUN yum -y install wget

# Jmeterのインストール
#RUN yum -y install java
#RUN wget https://ftp.kddi-research.jp/infosystems/apache//jmeter/binaries/apache-jmeter-5.3.tgz
#RUN tar xvf apache-jmeter-5.3.tgz

# 以下デスクトップ不要
# XRDPをインストール
#RUN curl -OL https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
#RUN rpm -Uvh epel-release-latest-7.noarch.rpm
#RUN yum -y install xrdp tigervnc-server

# GNOMEをインストール
#RUN yum -y groupinstall "GNOME Desktop"