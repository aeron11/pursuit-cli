# PURSUIT CLI

CLI for the PURSUIT framework.

> PURSUIT: A Fast Front-end Framework Based on Regular UI.
>
> web`P`ack + g`U`lp + `R`egular + mcs`S` + rg`UI` + s`T`ateman
> 
> babel + es6 + karma + mocha + expect.js

[![NPM Version][npm-img]][npm-url]
[![Dependencies][david-img]][david-url]
[![NPM Download][download-img]][download-url]

[npm-img]: http://img.shields.io/npm/v/pursuit-cli.svg?style=flat-square
[npm-url]: http://npmjs.org/package/pursuit-cli
[david-img]: http://img.shields.io/david/rainfore/pursuit-cli.svg?style=flat-square
[david-url]: https://david-dm.org/rainfore/pursuit-cli
[download-img]: https://img.shields.io/npm/dm/pursuit-cli.svg?style=flat-square
[download-url]: https://npmjs.org/package/pursuit-cli

## Install

```shell
npm install -g pursuit-cli
```

## Commands

- `pursuit help`：查看帮助
- `pursuit init <repo>`：初始化一个仓库

以下命令在仓库目录下运行：

- `pursuit build`：构建项目。需要将入口MCSS文件和JS文件放置在`src/page`目录中。
- `pursuit doc`：生成文档（待完善）。需要将Markdown文档写在每个组件的`demo`目录中。
- `pursuit test`：运行测试。需要将单元测试写在每个组件的`test`目录中。
- `pursuit lint`：验证代码风格。需要在运行目录中配置`.eslintrc`文件。
    - `-f, --fix`：验证时自动修复
- `pursuit icon`：生成雪碧图（CSS Sprites）和字体图标（Font Icons）。需要将雪碧图的原始图标放在`src/icons/png`目录中，运行命令后，雪碧图会生成在`dest/img`目录中，对应的CSS会生成在`src/icons/css`目录中；需要将字体的原始图标放置在`src/icons/svg`目录中，运行命令后，字体和预览网页会生成在`dest/fonts`目录中，对应的CSS会生成在`src/icons/css`目录中。
    目前的已知问题：
    - 只支持从一个svg文件夹生成字体图标；
    - 只支持在Mac和Linux环境下生成字体图标，并且需要安装以下包，详见：[FontCustom](https://github.com/FontCustom/fontcustom/#installation)；
    ```shell
    # On Mac
    brew install fontforge --with-python
    brew install eot-utils
    gem install fontcustom
    ```

- `-w, --watch`：监听文件变更。以上命令都可以配置此选项（默认不会监听）。
- `-v, --verbose`：输出详细信息
- `-V, --version`：当前版本

集成命令：

- `pursuit dev`：构建项目+生成文档+验证代码风格，始终监听文件，自动修复lint问题。相当于`pursuit build,doc,lint --watch --fix`。考虑到`icon`命令使用频率不高，并且某些开发者在Windows下无法使用，所以暂不加入`dev`命令中。
- `pursuit clean`：手动清理所有pursuit命令生成的文件（以上命令默认不会清理生成的文件）。相当于`pursuit build-clean,doc-clean,test-clean,icon-clean`。
- `pursuit online`：清理文件->生成图标->构建项目->运行测试->验证代码风格，永不监听文件。相当于`pursuit clean->icon->build->test->lint`。
