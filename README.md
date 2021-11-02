# MINECRAFT.NET-TRANSLATIONS

Minecraft 官方网站博文目录，收录全部分类的官网博文，以及社区投稿的博文译文。

在 2020 年 3 月 18 日前发布的部分新闻、市场类博文可能不会被收录。

本目录所收藏的博文翻译来自社区。如果你对自己翻译的质量有信心，欢迎向本仓库投稿。

推荐的博文目录浏览器：https://spxfellow.github.io



## 投稿须知

* 自 2021 年 7 月 7 日起，本仓库重新收录 MCBBS 的博文。
* 如果希望投稿，请在本仓库发起 issue 或 pull request.
* 如果您认为您的译文质量高于某译文，可以选择提出 issue 来申请替换。



## 文件结构

* `articles.csv`：存放所有博文及翻译。
* `mcContent.py`：运行这个脚本后，会将官网上的新博文同步到上述表格中。
* `cat.json`：分类名称对照表。
* `archive/`：MCBBS 译文归档。



## 使用指南

### 表格更新

在 2021 年 7 月 2 日，Minecraft.net 启用了防爬虫机制，直接爬取博文列表会失败。自 2021 年 8 月 28 日起，本仓库通过外部支持重新恢复了自动抓取功能。

若您希望手动更新表格，请参照如下方法：

#### 手动更新

1. 打开`https://www.minecraft.net/content/minecraft-net/_jcr_content.articles.grid?pageSize=100`，将其另存为一个名为`_jcr_content.articles.json`的文件。

2. 在命令行中运行`mcContents.py`，并加入参数以启用本地读取的方式：

   ```
   python ./mcContents.py local
   ```

#### 使用自己搭建的 API 网址

与手动更新类似，但是需要将 `local` 改为您的 API 网址：

```
python ./mcContents.py https://www.example.com/?src=content/minecraft-net/_jcr_content.articles.grid?pageSize=100
```



### 与 MCBBS 同步

`sync.py` 提供了与 MCBBS 新闻版同步的功能。惟请注意：

* 只能同步 Java 版本更新资讯/部分基岩 Beta 版更新资讯，且必须采用版规规定的标题格式，以解析该帖子所对应的版本。
* 翻译版是什么贵物？以后再说吧。

若想要开始同步，请直接运行脚本：

```
python .\sync.py
```





### 表格字段说明

* published - 发表日期
* title - 文章标题
* link - 原文链接
* cat - 文章分类，多分类以冒号分隔。分类名含义见 `cat.json`
* tr_title - 译文标题
* tr_link - 译文链接



### 表格内容编辑

如果你想在`articles.csv`中添加或编辑译文信息，推荐使用 VSCode 的 [janisdd.vscode-edit-csv](http://marketplace.visualstudio.com/items?itemName=janisdd.vscode-edit-csv) 插件。

除非你知道自己在做什么，**不要**使用 Excel 等软件，这将导致包括乱码在内的问题。



## 更新记录

* 2021-11-02 v3.6
  * 修复了一个问题，现在旧博文/已经出现过在列表中的博文不会再次被加入了。
* 2021-09-25 v3.5
  * 移除了 sync.py 对翻译版博文的同步功能。
  * 增加了 sync.py 对基岩测试版的同步功能。
  * 增加了对基岩测试版、半月建筑挑战的分类支持。
* 2021-08-31 v3.4
  * 稍微修改了 mcContents.py 的参数设置。
  * 美化了 mcContents.py 的代码结构，使其具备更高的可读性。
  * 修复了依然会收录 education.minecraft.com 的漏洞。
* 2021-08-18 v3.3
  * 扩充了 syncVersion.py 的功能，现在可以同步翻译版的已获得宝石评分的博文。
  * 将 syncVersion.py 重命名为 sync.py
* 2021-06-02 v3.2
  * 修复了一个漏洞，这个漏洞导致预发布版和候选版本的同步失败。
* 2021-05-13 v3.1
  * 加入了版本记录自动同步功能。现在，仓库每周四 23:59 UTC 会从 MCBBS 新闻资讯板块同步当前 Java 版本的更新记录。
* 2021-02-10 v3.0
  * 全新目录，堂堂连载！
  * 归档了所有 MCBBS 上的译文。
  * 新版本的表格 `articles.csv` 。
    * 译文链接与译者字段均保留，但是移除 MCBBS 相关的译者 uid 、绿宝石项目。
    * 现在接受除 MCBBS 帖子外的投稿。
  * `render`  和 `update` 功能，及其相关文件均被移除，因为有强大的 [S P X](https://spx.spgoding.com) 提供了高级的排版与搜索功能。
  * 由于现在只剩一个 `pull` 了，所以取消了运行参数。现在只需要 `python mcContents.py` 就可以拉取博文。 
  * 拉取博文会自动添加`botw`, `ti`, `atb`, `version` 分类了。
* 2020-01-14 v2.0
  * 跟随 MCBBS 官方博文录更新而做出了更新
* 2019-03-15 v1.2
  * 现在支持在运行脚本时填写一个参数，填写后将从此参数指向的网页中读取数据。
  * 取消了链接文字周围的尖号。（这项功能原本是为了非纯文本模式下的编辑，但是效果不好，建议一直使用纯文本编辑）
  * 修复了因官网前端更改导致的部分功能失效问题。
* 2018-12-10 v1.1
  * 添加了对表格、按钮元素的支持。
  * 修改了列表的格式。
    - 现在有序列表不再使用论坛内嵌代码，而是用无序列表配合计数器表示。
    - 现在会在条目下方附上原文，以供翻译，不再另起列表。
  * 修改了普通文段的预留文字。现在链接将单独表示出来，方便修改。
  * 将链接的颜色修改为了绿色。
  * 修改了英文原文的字号以及颜色。字号是可调的。（技术性提示：在代码中统一使用了color=Silver）
  * 现在将支持进入快照、预发布版和正式版的模式。考虑到臃肿问题，没有加入发布模板。
  * 修复了编码问题。现在应该不会再有编码问题导致的运行出错了。
  * 修复了快照模式下服务端框布局不对的问题
  * 修复了贡献者信息的标点问题。
* 2018-11-06 v1.0
  * 发布，并在发布后补上了代码内尖括号转义、视频封面图的支持，以及快照漏洞列表list没有关闭的漏洞 
