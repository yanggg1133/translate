<h1 align="center">Translate</h1>
<p align="center">
<a href="https://travis-ci.org/mouyong/translate"><img src="https://travis-ci.org/mouyong/translate.svg?branch=master" alt="Build Status"></a>
</p>

# Requirement

```
PHP >= 5.5
```

# Installation

```shell
$ composer require "mouyong/translate" -vvv
```

# Usage


```php
<?php

use Yan\Translate\TranslateManager;

$config = [
    'default' => 'google',

    'drivers' => [
        // 留空
        'google' => [
            'app_id' => '',
            'app_key' => '',
        ],
        
        'baidu' => [
            'ssl' => true,
            'app_id' => 'your-baidu-app_id',
            'app_key' => 'your-baidu-app_key',
        ],

        'youdao' => [
            'ssl' => false,
            'app_id' => '你的有道智云 应用ID',
            'app_key' => '你的有道智云 应用密钥',
        ],

        // 留空
        'jinshan' => [
            'app_id' => '',
            'app_key' => '',
        ]
    ],
];

$translate = new TranslateManager($config);

$result = $translate->driver()->translate('测试', 'zh', 'en');
$result = $translate->driver('google')->translate('测试', 'zh', 'en');
$result = $translate->driver('baidu')->translate('测试', 'zh', 'en');
$result = $translate->driver('youdao')->translate('测试', 'zh', 'en');
$result = $translate->driver('jinshan')->translate('测试', 'zh', 'en');

var_dump($result);
var_dump($result->getSrc());
var_dump($result->getDst());
var_dump($result->getOriginal());
```


MTrans 项目介绍
本项目 多源翻译 (Multi-source Translation, MTrans)，提供了集多种主流的 在线翻译 及 TTS 功能于一身的轻量级服务。通过程序向所支持的在线目标服务器发送 HTTP 请求，获取并解析返回的结果，为使用者提供便利。目前，本项目免费开源，开发者可基于此进行二次开发。

目前支持 源 及 语种 如下:

翻译源	服务器地址	支持语种	方式
百度翻译	http://fanyi.baidu.com/v2transapi	中文、英语、日语、韩语、法语、俄语、德语	互译
有道翻译	http://fanyi.youdao.com/translate_o	中文、英语、日语、韩语、法语、俄语	互译
谷歌翻译	https://translate.google.cn/translate_a/single	中文、英语、日语、韩语、法语、俄语、德语	互译
腾讯翻译君	http://fanyi.qq.com/api/translate	中文、英语、日语、韩语、法语、俄语、德语	互译
欧米翻译	http://www.omifanyi.com/transSents.do	中文、英语	互译
TryCan	http://fanyi.trycan.com/Transfer.do	中文、英语	互译
金山爱词霸	http://fy.iciba.com/ajax.php?a=fy	中文、英语、日语、韩语、法语、德语	互译
搜狗翻译	http://fanyi.sogou.com/reventondc/translate	中文、英语、日语、韩语、法语、俄语、德语	互译
TTS 源	服务器地址	支持语种
百度 TTS	http://fanyi.baidu.com/gettts	中文、英语、日语、韩语、法语、俄语、德语、泰语
有道 TTS	http://tts.youdao.com/fanyivoice	英语、日语、韩语、法语
谷歌 TTS	https://translate.google.cn/translate_tts	中文、英语、日语、韩语、法语、俄语、德语
腾讯 TTS	http://audiodetect.browser.qq.com:8080/tts	中文、英语、日语、韩语
搜狗 TTS	http://fanyi.sogou.com/reventondc/synthesis	中文、英语
