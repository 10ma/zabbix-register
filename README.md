# Zabbix-Register

- 監視対象へzabbix-agentを導入
- zabbix_agentd.conf, userparametersを設定
- Staging/Production Zabbix-Serverへの監視登録



## Usage

### Register for staging.

```shell
ansible-playbook -i hosts site.yml
```



### Register for production.

```shell
ansible-playbook -i hosts site.yml --extra-vars "stage=prod"
```



## Roles

- install
- setting
- monitor



## Author

@10ma
