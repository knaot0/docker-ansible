FROM ubuntu

# 初回のSSHアクセス時にホスト鍵のチェックを回避
# export ANSIBLE_HOST_KEY_CHECKING=False
ENV ANSIBLE_HOST_KEY_CHECKING False

# Ansibleのインストール
RUN apt-get update && \
    apt-get install -y software-properties-common && \
    apt-add-repository ppa:ansible/ansible && \
    apt-get update && \
    apt-get install -y ansible

CMD /bin/bash
