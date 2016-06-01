# 公共CDN的API

Root: `/v1/<cdn>/libraries`

支持 `jsdelivr`, `google`, `cdnjs`, `bootstrap`, and `jquery`.

只得到请求允许。没有设置限制。

把所有托管库JSON格式

```
http://api.jsdelivr.com/v1/jsdelivr/libraries
http://api.jsdelivr.com/v1/google/libraries
http://api.jsdelivr.com/v1/cdnjs/libraries
http://api.jsdelivr.com/v1/bootstrap/libraries
http://api.jsdelivr.com/v1/jquery/libraries
```


获取一个单一的库的基础上 `name` 参数.

```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jquery
http://api.jsdelivr.com/v1/jsdelivr/libraries/jquery - alias
```

获得任何图书馆的全部信息 `jq` 有结尾最新版本 `0.1`. [minimatch](https://www.npmjs.org/package/minimatch) 语法支持.

```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jq*&lastversion=*.0.1
```

您可以使用下列任何参数来搜索库。的搜索将匹配您的输入项目进行。可以同时使用多个参数。如果有多个项目匹配他们都将所输出的。

* `name` -库名称。 例: jquery
* `mainfile` - 在info.ini主文件参数。 例: jquery.min.js
* `lastversion`- 最新版本的项目。 例: 2.0.3 (will match multiple projects)
* `versions` -  所有托管的版本选定的项目. (read only)
* `description` - 项目介绍
* `homepage`- 网页工程。 例: http://jquery.com/
* `github`- 项目的GitHub页面 例: https://github.com/jquery/jquery
* `author` - 笔者项目。 例: jQuery Foundation
* `assets` - 每版本的文件。（只读）


您可以使用参数结合上面的参数 `fields`. 这样，您就可以控制输出。例如，以获得 `mainfile` jQuery的你会运行下面的请求。

```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jquery&fields=mainfile
```


这是可能的设置采用分离逗号多个字段。

```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jquery&fields=mainfile,name
```

获得托管每个版本的文件的jQuery
```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jquery&fields=assets
```

获得托管文件选定的版本
```
http://api.jsdelivr.com/v1/jsdelivr/libraries/jquery/2.0.3
```

获取库匹配查询的任何部分（默认为 `and`)
```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jquery&op=or
```
