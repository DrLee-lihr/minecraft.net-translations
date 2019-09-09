# minecraft.net-translations
## 说明

目前只维护Culture和Insider分类。运行mcContents.py即可在culture.csv和insider.csv追加新发布的博文。

MCBBS的官方博文录目前的收录更新到2018年6月3日《每周方块：音符盒》及其之前的帖子，这些帖子暂时不再同步到这里，请到论坛帖子中搜索。（但是也可能出现老文章后翻译的情况）

如果API坏了，请联系https://github.com/SPGoding

## 使用方法

### 更新数据

在目录下执行：

```bash
python mcContents.py [gb18030|utf-8]
```

不填写sync时，从官网更新数据到两个表中。

填写sync时，将两个表中的内容同步为参数中指定编码表的内容。

如，`python mcContents.py utf-8`将gb表同步为utf8表的内容。

### 添加内容

gb表支持使用excel编辑，utf8表支持使用主流文本编辑器（vscode, notepad++）编辑。

## 实用链接
在线博文转换器：https://spgoding.com

MCBBS官方博文录：https://www.mcbbs.net/thread-675773-1-1.html


