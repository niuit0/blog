# Nginx使用fancyindex索引

## fancyindex简介

> nginx自带的索引功能很单一，界面也很原始。后面有人做了个fancyindex的插件用来强化这个功能，已经被官方采用。

- 官方文档地址：<https://www.nginx.com/resources/wiki/modules/fancy_index/>
- 源码地址：<https://github.com/aperezdc/ngx-fancyindex>

## 使用fancyindex

1. 在编译Nginx时添加参数
    ```shell
    ./configure ... --add-module=../ngx-fancyindex
    make && make install
    ```

2. fancyindex指令
   - 使用fancyindex：`fancyindex on;`
   - 不显示精确大小：`fancyindex_exact_size off;`
   - 使用本地时间：`fancyindex_localtime on;`
   - 文件名最大长度：`fancyindex_name_length 255;`