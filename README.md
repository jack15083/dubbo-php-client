# dubbo-php-client

dubbo-php-client 是基于[crazyxman/dubbo-php-framework](https://github.com/crazyxman/dubbo-php-framework)抽取出的dubbo调用客户端，本项目只保留了dubbo客户端调用所需要的代码，重写了部分获取服务端地址逻辑
使调用不依赖swoole和服务端agent代理，直连zookeeper获取服务地址, 调用更简单方便, rpc请求改用PHP原生不依赖swoole client。所以不需要安装swoole扩展。
