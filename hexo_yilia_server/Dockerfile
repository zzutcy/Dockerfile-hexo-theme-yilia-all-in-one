FROM centos
MAINTAINER zzutcy "zzutcy@gmail.com"
ENV REFRESHED_AT 2018-11-16
RUN mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak

ADD CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo
ADD nginx-release-centos-7-0.el7.ngx.noarch.rpm /root/
ADD nginx.conf /etc/nginx/nginx.conf
ADD default.conf /etc/nginx/conf.d/

RUN rpm -ivh /root/nginx-release-centos-7-0.el7.ngx.noarch.rpm    \
    && yum makecache   \
    && yum update -y   \
    && yum install wget git nginx vim openssh-server net-tools -y   \
    && useradd git  \
    && mkdir -p /var/www/hexo  \
    && chown -R git.git /var/www/hexo \
    && su git  \
    && git init --bare hexo.git

ADD post-receive /home/git/
RUN mv /home/git/post-receive /home/git/hexo.git/hooks/post-receive \
    && chmod +x /home/git/hexo.git/hooks/post-receive  \
    && chown -R git.git /home/git 

EXPOSE 80 22
CMD ["/usr/sbin/nginx -s reload"]
