# vagrant-docker-wordpress

Dockerを利用してWordPressを簡単に立ち上げることができるUbuntu(14.04LTS)サーバ

## 使い方

- 初回のみ ansible でのパッケージインストールが必要です。

```
[local] $ vagrant up
[local] $ vagrant ssh
[guest] $ cd /vagrant/ansible-playbook
[guest] $ ansible-playbook docker-host.yml
[guest] $ exit
```

Dockerのコンテナを起動します。
この手順は毎回必要となります。
```
[local] $ vagrant ssh
[guest] $ cd /vagrant
[guest] $ docker-compose up -d

[local] open browser http://192.168.33.11/ and set up wordpress.
```


## WordPressのデータ一式について

- WordPressのデータは `/vagrant/html` 以下に自動的に展開されます。
- バージョンは 4.7系の英語版となります。

## PHPのバージョンについて

- PHP 7.1.x を利用しています。
