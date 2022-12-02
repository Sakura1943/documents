# Rust Language
> 记录一些`rust`的常用`crates`库， 以及平时遇到问题的处理方法等
----
- # 常用`crates`库
  - ## `serde`
    序列化与反序列化库
    - 常用`features`:
      - `derive`: 提供给`derive`使用的宏

  - ## `serde_json`
    处理使用了`serde`提供的`Serialize`和`Desrialize`宏的`crates`库, 可将文字符串列化为自定义数据或者`json`数据，也可将数据反序列化为字符串

  - ## `json`
    `json`数据反序列化和序列化库

  - ## `poem`
    `web`后端框架

  - ## `sea-orm`
    `rust`较为好用的orm

  - ## `clap`
    `CLI` 编写库
    - 常用`features`:
      - `derive`: 提供给`derive`使用的宏

  - ## `clap_complete`
    `clap`的命令补全脚本生成器

  - ## `reqwest`
    常用的http client
    - 常用`features`:
      - `json`: 提供json数据序列化和反序列化方法
      - `cookies`: 提供`cookie`存储方法

  - ## `anyhow`
    万能`Result`处理库

  - ## `thiserror`
    自定义`Error`库， 配合`anyhow`使用，体验更佳

  - ## `once_cell`
    用于存储`堆`上的信息，最多可初始化`一次`

  - ## `tokio`
    异步运行时
    - 常用`features`:
      - `macros`: 提供异步宏,
      - `rt-multi-thread`: 提供异步多线程的支持

  - ## `dialoguer`
    命令行提示库, 配合`console`使用效果更佳
  
  - ## `console`
    终端和控制台抽象库

  - ## `rust-embed`
    文件嵌入编译结果的库(将文件转换为`bytes`)

  - ## `rand`
    随机数生成库

  - ## `toml`
    `toml`文件操作库

  - ## `subprocess`
    提供命令行执行的子命令和管道执行的封装