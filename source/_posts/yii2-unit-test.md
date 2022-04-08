---
title: yii2-unit-test
date: 2022-04-08 15:29:29
tags: 
    - Yii2
    - phpUnit
---
# 测试

[文档](https://codeception.com/for/yii)

在项目目录执行

### 生成测试

```
vendor/bin/codecept generate:test unit models/KnowledgeModelTest -c frontend
```

### 执行测试

```
vendor/bin/codecept run unit models/KnowledgeModelTest -c frontend
vendor/bin/codecept run unit models/KnowledgeModelTest:testSave -c frontend //具体方法
```

### fixture 生成测试数据

```
1、新建template 
路径：common/fixtures/templates/QaKnowledgeModels.php
<?php
$faker = \Faker\Factory::create();
return [
    'title'=> $faker->name,
    'product_id' => 1,
    'forth_status' => rand(1,2),
    'created_at'=>time(),
];

2、配置修改
console/config/main.php
 'controllerMap' => [
        'fixture' => [
           // 'class' => 'yii\console\controllers\FixtureController',
            'class' => 'yii\faker\FixtureController',
            'namespace' => 'common\fixtures',
            'templatePath' => '@common/fixtures/templates',
            'fixtureDataPath' => '@common/fixtures/data',
          ],
    ],

3.执行命令
php yii fixture/generate QaKnowledgeModels --count=10
```


### 断言

[PHPUnit](https://phpunit.de/manual/6.5/en/appendixes.assertions.html)
```
$this->assertEquals()
$this->assertContains()
$this->assertFalse()
$this->assertTrue()
$this->assertNull()
$this->assertEmpty()
```
