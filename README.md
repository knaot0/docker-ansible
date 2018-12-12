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
4. inventry, playbookファイルがあるディレクトリに移動
```
cd /var/data
```
5. target01, target02に対し、sshの接続確認
```
ssh target01    (yesで接続)
exit
ssh target02    (yesで接続)
exit
```
6. target01, target02に対し、ansibleコマンドを実行
```
ansible-playbook -i inventry.ini playbook.yml
```
7. target01, target02に再接続し、hogeが追加されていることを確認
```
ssh target01
ls
exit
ssh target02
ls
```


## dockerコマンド
- 起動コマンド
```
docker-compose up -d
```
- 停止コマンド
```
docker-compose stop
```
- 停止+削除コマンド
```
docker-compose down
```
- コンテナに接続
```
docker exec -it [コンテナ名orID] sh
```
- オプション
```
-d : バックグラウンド実行
```

## ansibleコマンド
- 標準コマンド
```
cd ansible/
ansible-playbook -i inventry.ini playbook.yml
```
- 構文チェック
```
ansible-playbook playbook.yml --syntax-check
```
- ログ出力
```
ansible-playbook -i inventry.ini playbook.yml -v
ansible-playbook -i inventry.ini playbook.yml -vv
ansible-playbook -i inventry.ini playbook.yml -vvv
```
- オプション
```
-i             : inventryファイルを指定
-step          : step実行 (y: 実行, n: スキップ, c: 全て実行) 
--syntax-check : ymlファイルの構文チェック
```

## 正規表現チェッカー
http://www.rubular.com/