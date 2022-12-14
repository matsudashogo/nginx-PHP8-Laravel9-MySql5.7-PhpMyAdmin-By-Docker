# nginx-PHP8-Laravel9-MySql5.7-PhpMyAdmin-By-Docker

## 構築環境
```
・nginx
・PHP 8.0
・MySql 5.7
・Laravel9
・PhpMyAdmin
```

## clone後設定
clone後にプロジェクトのRootディレクトリで以下を実行

### docker build
```shell
$ docker-compose up -d
```

### MySql
```shell
$ docker-compose exec db bash
$ mysql -u root -p # パスワードはdocker-compose.ymlで指定したMYSQL_ROOT_PASSWORD
$ CREATE DATABASE {DB名} # DB名はdocker-compose.ymlで指定した、MYSQL_DATABASEと合わせる
$ exit
```

### Laravel
```shell
$ docker-compose exec php bash
$ cd laravel9
$ cp .env.example .env
$ composer install
$ php artisan key:generate
$ exit
```

### Laravelのプロジェクトファイル内の.envファイルを下記に修正
```.env:title
DB_CONNECTION=mysql
DB_HOST=db # docker-compose.ymlに記載したDBのサービス名
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=docker
DB_PASSWORD=docker
```

### http://localhost にアクセス