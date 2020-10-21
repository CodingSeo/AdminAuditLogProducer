# Admin Audit Log Builder

## 설명
어드민 감사 이벤트 처리 Json String Builder

## Install
```composer log
"require": {
        "hiworks/admin-audit-log-builder": "^1.0"
}
```
## Requirement

myclabs/php-enum : 1.6.6

hiworks/kafka-producer : 1.0.4

## Usage
> **Note:** This version of this SDK for PHP requires **PHP 5.6** or greater.

```php
try {
     $admin_audit_log = AdminAuditLog::builder()
                   ->setMenu(MenuCodeType::APPROVAL)
                   ->setLevel(LevelType::A)
                   ->setAccessIp('127.0.0.1')
                   ->setHost('127.0.0.1')
                   ->setUserName('김**')
                   ->setOfficeNum(123)
                   ->setUserId('test_user')
                   ->setUserNum(123)
                   ->setEngFullMessage('This is Full Eng Message')
                   ->setEngMessage('This is Short Eng Message')
                   ->setShortMessage('This is Short Kor Message')
                   ->setFullMessage('This is Full Kor Message')
                   ->build();
 }
 catch (Exception $e){
     //Arguments that's not filled in the builder will be stacked here.
     var_dump($e->getMessage());
 }
```
## 


## Test Cases
>./vendor/bin/phpunit --testsuite builder

admin_audit_log_builder testing (validation, json-string format)

>./vendor/bin/phpunit --testsuite send

send admin_dto by Kafka-producer

>./vendor/bin/phpunit --testsuite get

get message by Kafka-consumer
