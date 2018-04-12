# zmake
auto configure framework, by embed make flags into source file.

## Table of contents
* [License](#license)
* [Usage](#usage)
  * [Welcom to zmake](#welcome-to-zsi)
* [Enjoy zmake](#enjoy-zsi)

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

### build
- 拷贝configure到有zmake标签的项目目录，执行configure即可生成Makefile；

### benefit
- 学习成本低，8个标签，3分钟学会；
- 支持任意复杂的c/c++项目类型（目标）；
- 时间成本低，定制性强，编写快速只需在项目必要的c/c++文件中添加1~4个标签即可；

### why not cmake or auto configure first
- 学习极高，对于复杂项目配置也极其复杂；

### why not support window
- please use visual studio

### sample
- https://github.com/ZRiemann/zsi
- https://github.com/ZRiemann/znt

### zmake tags
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

# Enjoy zmake

- Z.Riemann (original author)
