# Rust Language

> 记录一些`rust`的常用`crates`库， 以及平时遇到问题的处理方法等

---

- # 常用`crates`库
  - ## `serde`
    序列化与反序列化库
    - 常用`features`:
      - `derive`: 提供给`derive`使用的宏

  - ## `serde_json`
    处理使用了`serde`提供的`Serialize`和`Desrialize`宏的`crates`库,
    可将文字符串列反序列化为自定义数据或者`json`数据，也可将数据序列化为字符串

  - ## `json`
    `json` `parser`

  - ## `poem`
    `web`后端框架
  - ## `poem-openapi`
    提供`poem` `openapi`的支持

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
      - `json`: 提供json数据反序列化方法
      - `cookies`: 提供`cookie`存储桶

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

  - ## `tracing`
    日志打印库

  - ## `tracing-subscriber`
    日志订阅库

  - ## `tracing-appender`
    附加日志处理库

  - ## `ureq`
    一个简单，安全的`http client`
    - 常用`features`:
      - `json`: 提供`json`数据反序列化方法,
      - `cookies`: 提供`cookie`存储桶

  - ## `trauma`
    一个简单的`Downlaoder`下载器，有进度条显示(异步库)

- # 日志处理
  ```rust
  use anyhow::Result;
  use tracing_subscriber::{Registry, layer::SubscriberExt, util::SubscriberInitExt, fmt};
  use tracing_appender::{rolling::hourly, non_blocking};

  fn main() -> Result<()> {
    let file_appender = hourly("logs", "info.logs");
    let (file_non_blocking, _guard) = non_blocking(file_appender);
    let file_layer = fmt::layer()
        .with_ansi(false)
        .with_writer(file_non_blocking);
    let (stdout_non_blocking, _guard) = non_blocking(std::io::stdout());
    let formatter_layer = fmt::layer().with_writer(stdout_non_blocking);
    Registry::default()
        .with(formatter_layer)
        .with(file_layer)
        .init();
    build()?;
  }
  ```

- # 异步`future`编写
    ```rust
    use anyhow::Result;
    use std::future::Future;

    async fn future_fn<T, F>(f: F) -> Result<()>
    where
        T: Future<Output = Result<()>> + 'static,
        F: Fn(String) -> T,
    {
        f("name".to_owned()).await?;
        Ok(())
    }
    ```
