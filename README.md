# zmake
auto configure framework, by embed zmake flags into source file.

> 一个自动化生产Makefile脚步框架，基于在源码中嵌入zmake标签；

## Table of contents
* [License](#license)
* [Usage](#usage)
  * [Welcom to zmake](#welcome-to-zsi)
  * [Benefit](#benefit)
  * [Sample](#sample)
  * [Build application](#build-application)
  * [Build library](#build-library)
  * [Zmake tags](#zmake-tags)
  * [Directory](#directory)
* [Enjoy zmake](#enjoy-zmake)

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

## Usage

### Welcom to zmake

>   zmake 一个类似 auto configre 自动化生成 Makefile 项目。基于嵌入zmake标签到
> 源代码的方式，避免手动编写任何辅助脚步文件。
> CMake/auto-configure 耗费学习成本，编写复杂；

### Benefit
- 学习成本低，8个标签，3分钟学会；
- 支持任意复杂的c/c++项目类型（目标）；
- 时间成本低，定制性强，编写快速只需在项目必要的c/c++文件中添加1~4个标签即可；
- 免安装，不用安装第三方软件如auto config/cmake；只需要将configure拷贝到工程目录

### why not cmake or auto configure first
- 学习难道高，不易熟练掌握，对于复杂项目配置也极其复杂；

### why not support window
- visual studio 已经出神入化无需画蛇添足；

### Sample
- https://github.com/ZRiemann/zsi
- https://github.com/ZRiemann/znt


### Build application
- 拷贝configure到有zmake标签的项目目录，执行configure即可生成Makefile；
- 在main函数所在的原文件使用以下标签，注意：@zmake.app 必须在最下面一行(保留脚步的简洁，不做复杂处理)
```
/** zsi/test/tst_mtmain.c
 * 不生成安装脚步
 * @zmake.install off;
 * 默认编译生成目标可执行文件
 * @zmake.build on;
 * 依赖的同级别库;
 * @zmake.depso foo bar zsi;
 * @zmake.depar zsi;
 * 目标文件名, 必须在最后一行, 否则会增加configure脚本的不必要的容错代码。
 * @zmake.app tstmt;
 */
int main(){...}
```
- 在其他模块文件下只需要添加一个标签，关联到对于得可执行文件即可
```
/**
 *  作为tstmt目标的模块关联到tstmt;
 * @zmake.app tstmt;
 */
int tstmt_funs(){...}
int tstmt_othrers(){...}
```
### Build library
- 生成.so/.a库文件，只需在源码文件中添加一个@make.lib <libname> 标签即可；
```
/** *.c
 * @zmake.lib zsi;
 */
```

### Zmake tags
-  每个.c/c++源文件之需要添加一个标签即可，每个可执行程序目标选取一个文件附加少数其他标记；
-  @zmake.install [off|ON];          默认 ON, 标记是否生成 install，如库的测试程序可以不安装
-  @zmake.build [off|ON];            默认 ON, 标记是否被编译生成目标文件，如库的测试程序可以默认不生成
-  @zmake.link <-l...>;              目标程序的连接库，如 -lzsi -lpthread
-  @zmake.depso <lib1 lib2 ...>;     目标程序依赖的当前编译动态库，不标记make -j8可能失败
-  @zmake.depar <lib1 lib2 ...>;     目标程序依赖的当前编译静态库，不标记make -j8可能失败
-  @zmake.app <name>;                目标程序名称
-  @zmake.lib <name>;                目标库名称，同时生成动态库和静态库，如:libszi.so.1.0.0/libzsi.a
-  @zmake.ar <name>;                 目标库名称，只生成静态库，如:大型项目可以按模块生成静态库后链接

#### caution
- 每个标签必须以 ; 结尾，否则可能会生成出错;
- 一个文件被多个目标使用时，可以使用空格分隔多个目标，如 @zmake.lib zsi znt;
- 依赖多个同等编译酷是也使用空格分开，如 @zmake.depso zsi znt; 这样make -j8时就不会出现编译出错；

### Directory
- configure 脚步会自动搜索当前目录及其子目录下的所有c/c++源文件标签生成相应的Makefile
- 不建议在其同级目录及其子目录添加第三方库源码，否则会增加不不要的文件检索
- 建议所有代码放到同级目录下的 src/ 子目录，因为默认添加了 -I. -Isrc;如需其他路径，暂时手动修改

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
