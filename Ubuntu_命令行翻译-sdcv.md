[toc]

# sdcv - 命令行翻译工具

## 安装

```shell
sudo apt install sdcv
```

## 安装词库

[词典下载地址: http://download.huzheng.org/zh_CN/](http://download.huzheng.org/zh_CN/)

```shell
mkdir -p .stardict/dic
tar jxvf ~/Downloads/stardict-oxford-gb-formated-2.4.2.tar.bz2 -C ~/.stardict/dic/
tar jxvf ~/Downloads/stardict-oxford-gb-formated-2.4.2.tar.bz2 -C ~/.stardict/dic/
tar jxvf ~/Downloads/stardict-oald-cn-2.4.2.tar.bz2 -C ~/.stardict/dic/
tar jxvf ~/Downloads/stardict-langdao-ce-gb-2.4.2.tar.bz2 -C ~/.stardict/dic/
tar jxvf ~/Downloads/stardict-oxford-gb-2.4.2.tar.bz2 -C ~/.stardict/dic/

sdcv -l #查询安装的词典
```

