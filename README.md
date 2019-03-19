# zmake
auto configure framework, by embed zmake flags into source file.

> 一个自动化生产Makefile脚步框架

## Table of contents
* [Usage](#usage)
  * [Welcom to zmake](#welcome-to-zsi)
  * [Benefit](#benefit)
  * [Sample](#sample)
  * [Build application](#build-application)
  * [Build library](#build-library)
  * [Zmake tags](#zmake-tags)
  * [Directory](#directory)
* [Enjoy zmake](#enjoy-zmake)
* [License](#license)

## Usage

### Welcom to zmake

>   zmake 一个类似 auto configre 自动化生成 Makefile 项目。
> CMake/auto-configure 耗费学习成本，编写复杂；

### Benefit
- 学习成本低，只需简单配置zmake.conf的即可，少数几行配置即可量增式管理项目；
- 支持任意复杂的c/c++项目类型（目标）；
- 免安装，不用安装第三方软件如auto config/cmake；只需要将zmake,zmake.conf拷贝到工程目录
- 输出(默认./bin)与源码分离，避免中间文件混入源码目录中；
  bin/debug ; debug 输出
  bin/relase ; release 输出(已经strip)
- 自带install/uninstall脚本
- 自带版本控制功能 默认v1.0.0
### why not cmake or auto configure first
- 不易熟练掌握，对于复杂项目配置也极其复杂；

### why not support window
- visual studio 已经出神入化无需画蛇添足；

### Sample
- https://github.com/ZRiemann/zsi
- https://github.com/ZRiemann/znt


### Build application
- 拷贝[configure(可选)]zmake,zmake.conf到有zmake标签的项目目录，执行[configure] zmake 即可生成Makefile；
- 假设生成zsitst可执行程序
```
# 配置 zmake.conf
# 1. 将zsitst添加到 all 列表中
all=(
    zsi
    zsitst
)

# 2. 定义zsitst项目内容
# 自动检测头文件依赖
# 自动依赖 libzsi.so 目标
declare -A zsitst
zsitst=([type]=app
        [build]=yes
        [install]=false
        [headers]="test"
        [source]="test/main.c test/tst_fsio.c test/tst_s_expression.c test/tst_buffer.c test/tst_stl.c test/tst_app.c"
        [links]="-lzsi -pthread")

```
### Build library
- 生成.so/.a库文件
- 假设生存libzsiso + libzsi.a
```
# zmake.conf
# 1. 添加zsi 到 alloc
all=(
    zsi
)

# 2. 定义zsitst项目内容
declare -A zsi
zsi=([type]=so
     [build]=yes
     [install]=yes
     [install_headers]="src/zsi"
     [source]="src")

```

### version
#### v1.0.0
- 支持生成动态库和静态库
- 支持生成可执行文件
- 支持并发编译 make -jN
- 支持选择性编译
- 支持debug版和release版本并存

#### v1.0.1 TODO:
- 自动下载安装指定依赖库
- 支持命令行选项
- 追踪更深层次的头文件依赖关系
- 支持自动化测试标签

# Enjoy zmake

- Z.Riemann (original author)

## License

> MIT License
>
> Copyright (c) 2018 Z.Riemann
>
> Permission is hereby granted, free of charge, to any person obtaining a copy
> of this software and associated documentation files (the "Software"), to deal
> in the Software without restriction, including without limitation the rights
> to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
> copies of the Software, and to permit persons to whom the Software is
> furnished to do so, subject to the following conditions:

> The above copyright notice and this permission notice shall be included in all
> copies or substantial portions of the Software.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
> FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
> AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
> LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
> OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
> SOFTWARE.
