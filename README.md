# 系统学习composer组件开发案例

## 基本结构

```
weather/
├── .editorconfig   # 编辑器配置文件，比如缩进大小、换行模式等
├── .gitattributes  # git 配置文件，可以设计导出时忽略文件等
├── .gitignore      # git 忽略文件配置列表
├── .php_cs         # PHP-CS-Fixer 配置文件
├── README.md    
├── composer.json
├── phpunit.xml.dist
├── src
│   └── .gitkeep
└── tests
    └── .gitkeep
```

## 搭建创建工具（本人mac os）

* composer 全局安装 
```
composer global require 'chunpat/package-builder' --prefer-source
```
**运行后可能会出现依赖关系而失败，然后按需composer global require相关既可以**

安装成功后，创建第一个项目
```
~/.composer/vendor/chunpat/package-builder/bin/package-builder build ./weather
```

## src目录下写业务逻辑和异常或错误处理

参考代码

## 单元测试

> 规范

* 测试用例与类名对应，以 Test.php 结尾，比如 WeatherTest.php，类名与文件名一致；
* 测试用例需要继承 PHPUnit\Framework\TestCase 基类；
* 测试用例的目录结构与源码一致；
* 测试用例的方法名格式为 test源方法名，比如：testGetWeather。
* 测试用例，可以用已有的优秀组件，命令

> 安装单元测试框架

```
composer require phpunit/phpunit mockery/mockery
```

> 测试啥

** 全方位测试，如参数测试，逻辑测试，异常测试等用例**

执行命令
```
./vendor/bin/phpunit --filter testGetWeatherWithInvalid //测试某个用例， --filter testGetWeatherWithInvalid可以模糊批量执行

./vendor/bin/phpunit //测试整个用例

```

** 这里涉及到两个工具一个phpunit和mockery，链接在下 **
https://phpunit.readthedocs.io/zh_CN/latest/
http://docs.mockery.io/en/latest/

## 开发完组件后，在项目中如何使用

第一种开发完组件后上传到git仓库，然后在composer仓库中发布，最后本地的composer require安装建立关联映射。
第二种直接在本地，在composer.json文件加下面这条参数。
```
 "repositories": {
    "weather": {
        "type": "path",
        "url": "../weather" //组件路径
    }
  }
```

## 为Laravel继承优化

待补充

## 编写组件说明文档

待补充

## 发布

1、git仓库。2、composer仓库(https://packagist.org/)或者自建

## Travis-CI做自动化测试

待补充
https://travis-ci.org/

## 状态图标

待补充

## Style CI


## 参考资料
* 1、[LX2 PHP 扩展包实战教程 - 从入门到发布](https://learnku.com/courses/creating-package/)
* 2、[composer官方文档](https://docs.phpcomposer.com/03-cli.html)
