# docker-ansible

## ディレクトリ構成
```
.
├── README.md
├── docker
│   ├── ansible
│   │   └── Dockerfile      ansibleのDocerfile
│   └── target
│       └── Dockerfile      targetのDockerfile
├── docker-compose.yml      docker-composeファイル
├── inventry.ini            hostsファイル
└── playbook.yml            playbookファイル
```

## 使い方
1. Dockerコンテナの起動
```
docker-compose up -d
```
2. AnsibleのコンテナIDを確認
```
docker ps
```
3. Ansibleコンテナに接続
```
docker exec -it ansible
```
4. target01, target02に対し、sshの接続確認
```
ssh target01    # yesで接続
exit
ssh target02    # yesで接続
exit
```
5. target01, target02に対し、ansibleコマンドを実行
```
ansible-playbook -i inventry.ini playbook.yml
```
6. target01, target02に再接続し、hogeが追加されていることを確認
```
ssh target01
ls
exit
ssh target02
ls
```
