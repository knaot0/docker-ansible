# Amazon EC2
FROM amazonlinux:latest

# yumでOpenSSｈサーバをインストールする
RUN yum -y install openssh-server

# sshd起動時に公開鍵が必要なため、作成  2020/11 OpenSSH6.5以降楕円曲線Diffee Hellman鍵も追加 
RUN ssh-keygen -A


# rootでログインできるようにする
RUN sed -ri 's/^#PermitEmptyPasswords no/PermitEmptyPasswords yes/' /etc/ssh/sshd_config

# rootのパスワードを指定
RUN echo "root:" | chpasswd

EXPOSE 22

# sshdを起動
CMD ["/usr/sbin/sshd", "-D"]
