# Theme for Chopper Documentation

---

这是一个 从[nico-one](https://github.com/lepture/nico-one.git)修改的 [nico](http://lab.lepture.com/nico/) 主题。


## 安装


### 1. 安装 node

请自己安装 node。

### 2. 安装 chopper theme

Linux & Mac 用户一键安装：

```
curl https://raw.github.com/chopper-UI/spm-theme/master/boot.sh | sh
```

另外，如果你安装了 socket.io 的话，将有 livereload 功能。

```
$ npm install socket.io -g
```

Windows 用户安装：

在cmd下运行下面命令：

```
git clone https://github.com/chopper-UI/spm-theme.git "%HOMEDRIVE%%HOMEPATH%\.spm\themes\chopper
```

切换到`chopper`目录，把里面的`make.bat`文件复制到一个全局PATH下（保证make命令可用即可）

P.S. __注意千万别把`C:\Users\{{username}}\.spm\themes\chopper`目录设置为全局PATH，这样`nico`命令会失效，切记！__

## 使用说明

复制一份 [Makefile](https://github.com/chopper-UI/spm-theme/blob/master/Makefile) 到你的项目下：

Windows 用户可使用 [make.bat](https://github.com/chopper-UI/spm-theme/blob/master/make.bat)。


- `make build-doc` 用于生成文档。
- `make debug` 是开启本地服务器，可用来预览文档，并提供自动构建和 live reload 支持。(从本地 sea-modules 中加载依赖)
- `make watch` 是开启本地服务器，可用来预览文档，并提供自动构建和 live reload 支持。 (从线上加载依赖)
- `make server` 普通服务器，无自动刷新功能。
- `make publish` 发布站点到spmjs.org

Windows 用户注意，如果报错，说找不到 nico，请设置环境变量 `NODE_PATH`。
请根据实际情况自行解决，一般来说应该设置为：

```
NODE_PATH = C:\Users\{{username}}\AppData\Roaming\npm\node_modules
```

## 文档编辑

- http://lab.lepture.com/nico/zh/
- http://lab.lepture.com/nico/zh/syntax

nico 还会用到模块根目录下的 package.json 文件，具体项的含义请参考：[spm package.json](https://github.com/spmjs/spm/wiki/package.json)

其中 ``repository.url`` 用来生成 View the Project 链接， ``bugs.url`` 用来生成讨论链接。


### 特有功能

用三个 ` 会高亮显示代码

    ```js
    function something() {
    }
    ```

用四个 ` 会高亮显示代码，还会将代码插入到生成的 HTML 页面中

    ````js
    function something() {
    }
    ````

插入 iframe

    ````iframe
    <link rel="stylesheet" href="css/some.css">
    <button>click</button>
    <script>
        seajs.use('jquery', function($) {
            $('button').click(function() { alert('hello'); })
        });
    </script>
    ````

还可以设置 iframe 的高度

    ````iframe:400
    ````

生成 iframe 的模板是 `templates/iframe.html`，不用写头写尾。



## 输出

假设模块的目录结构为：

```
package.json
Makefile
src/
    hello-world.js
examples/
    hello-world.md
docs/
    hello-world.md
README.md
```

执行 `make build-doc` 后会生成：

```
package.json
Makefile
_site/
    index.html
    src/
        hello-world.js
    examples/
        hello-world.html
    docs/
        hello-world.html
src/
    hello-world.js
examples/
    hello-world.md
docs/
    hello-world.md
README.md
```

所有生成的文件都在 `_site` 目录下。


## 测试

