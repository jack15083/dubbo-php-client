# dubbo-php-client

dubbo-php-client 是基于[crazyxman/dubbo-php-framework](https://github.com/crazyxman/dubbo-php-framework)抽取出的dubbo调用客户端，本项目只保留了dubbo客户端调用所需要的代码，重写了部分获取服务端地址逻辑
使调用不依赖swoole和服务端agent代理，直连zookeeper获取服务地址, 调用更简单方便。


# 依赖扩展: 

zookeeper,bcmath, swoole


# 安装

composer require jack15083/dubbo-php-client:dev-master

# 调用

```
<?php

require_once '../vendor/autoload.php';

use DubboClient\Consumer\DubboConsumer;
//use Dubbo\Common\Protocol\Dubbo\DubboParam;

$consumerConfig = 'ConsumerConfig.yaml';
//第二个参数可选,如果设置会将解析后的yaml结果缓存到指定文件,下次调用将直接读取缓存，更改配置文件后一定要删除缓存文件！
$instance = DubboConsumer::getInstance($consumerConfig, null);
$service = $instance->loadService('com.ikurento.user.ExportProvider');//同一service只需加载一次
$res = $service->invoke('GetExportTplByTplName',['tplName' => 'order']); //多个参数

/*

// When the argument is an Integer
$service = $instance->loadService('com.imooc.springboot.dubbo.demo.IntegerDemoService');
$res = $service->invoke('sayHello', 20880);

// When the argument is an String
$service = $instance->loadService('com.imooc.springboot.dubbo.demo.StringDemoService');
$res = $service->invoke('sayHello', "hello");

// When the argument is an Map
$service = $instance->loadService('com.imooc.springboot.dubbo.demo.MapDemoService');
$res = $service->invoke('sayHello', ['a'=>'b']);

// When the argument is an ArrayList
$service = $instance->loadService('com.imooc.springboot.dubbo.demo.ArrayListDemoService');
$res = $service->invoke('sayHello', [2,3,4]);

// When the argument is an LinkedList
$service = $instance->loadService('com.imooc.springboot.dubbo.demo.LinkedListDemoService');
$res = $service->invoke('sayHello', DubboParam::Type('java.util.LinkedList', ['a', 'b']));

// When the argument is an object
$service = $instance->loadService('com.imooc.springboot.dubbo.demo.ObjectDemoService');
$res = $service->invoke('sayHello',
    DubboParam::object(
        'com.imooc.springboot.dubbo.demo.dto.TestObjectDemo',
        [
            "name" => "Tom",
            "age" => 30,
            'bigDecimal' => DubboParam::object('java.lang.Object', ['value' => 15.6])
        ])
);

 */
```
