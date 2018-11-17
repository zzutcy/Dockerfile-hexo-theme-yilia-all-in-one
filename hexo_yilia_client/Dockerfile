FROM centos
MAINTAINER zzutcy "zzutcy@gmail.com"
ENV REFRESHED_AT 2018-11-15
RUN mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak

ADD CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo

RUN yum update -y   \
    && yum install wget git vim -y     \
    && wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo   \
    && yum update -y   \
    && yum install nodejs -y   \
    && npm config set registry http://registry.npm.taobao.org/  \
    && npm install -g hexo-cli  \   
    && cd /root    \
    && git clone https://github.com/zzutcy/hexo-theme-yilia-all-in-one.git     \
    && cd hexo-theme-yilia-all-in-one/     \
    && hexo clean

EXPOSE 4000