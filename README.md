# Zabbix-Register

- Zabbix-ServerでPSKファイルの作成
- 監視対象へzabbix-agentを導入
- zabbix_agentd.conf, userparametersを設定
- Staging/Production Zabbix-Serverへの監視登録



## Require host

- [zabbix-master]
- [agent-servers], [proxy-servers], [local-agent-servers]



## Usage

### Edit inventory host file

```shell
$ pip install zabbix-api
$ vi hosts
```

```ini
[zabbix-master]
zabbix2-master-server
```

- `zabbix-master` group・・・Zabbix-Server IP or hostname.



### Register for staging.

```shell
ZABBIX_LOGIN_USER=[xxx] ZABBIX_LOGIN_PW=[xxx] ansible-playbook -i hosts site.yml
```



### Register for production.

```shell
ZABBIX_LOGIN_USER=[xxx] ZABBIX_LOGIN_PW=[xxx] ansible-playbook -i hosts site.yml --extra-vars "stage=prod"
```



## Roles

- create-psk - `zabbix-master` サーバーで `psktool` で `full_psk`, `key_psk`を作成、Download
- install -  Distribution別にZabbix-SIAレポジトリ導入して `zabbix-agent`をインストール
- setting - zabbix-agentd.confや監視系ファイルを設置
- monitor - zabbix-server側にホストグループ・ホスト登録のAPIを投げる



## Author

@10ma
