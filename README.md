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

# Enjoy zmake

- Z.Riemann (original author)
