# Bitbucket Pipelines PHP 8.2 image

[![](https://images.microbadger.com/badges/version/pyguerder/bitbucket-pipelines-php82.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php82 "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/pyguerder/bitbucket-pipelines-php82.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php82 "Get your own image badge on microbadger.com")

## Based on Ubuntu 22.04

### Packages installed

- `php8.2-zip`, `php8.2-xml`, `php8.2-mbstring`, `php8.2-curl`, `php8.2-json`, `php8.2-imap`, `php8.2-mysql`, `php8.2-tokenizer`, `php8.2-xdebug`, `php8.2-intl`, `php8.2-soap`, `php8.2-pdo`, `php8.2-cli`, `php8.2-apcu`, `php8.2-redis` and `php8.2-gd`
- wget, curl, unzip
- Composer 2
- Mysql 8
- Node 16 + Yarn

### Sample `bitbucket-pipelines.yml`

```YAML
image: pyguerder/bitbucket-pipelines-php82
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost -u root -proot -e "CREATE DATABASE test;"
          - composer install --no-interaction --no-progress --prefer-dist
          - ./vendor/phpunit/phpunit/phpunit -v --coverage-text --colors=never --stderr
```
