# duoshuo2disqus

# 背景 #

前几天我受够了多说的各种漏洞和问题，终于把评论系统切换到了 Disqus。为了尽可能的保留之前网友们的留言和评论，我写了个 Python 程序把多说导出的 JSON 格式文件转换成了 Disqus 支持的 WXR (WordPress eXtended RSS) 格式。

对切换评论系统的前因后果以及中间过程感兴趣的话，可以看看我之前的博文《[告别多说，拥抱 Disqus](http://blog.jamespan.me/2015/04/18/goodbye-duoshuo/)》。

可以访问我的博客原文《[我把博客评论从多说迁移到 Disqus 时造的轮子](http://blog.jamespan.me/2015/04/21/the-duoshuo-migrator/)》参与讨论。

# 轮子 #

代码明显属于糙快猛的风格，没有太多的讲究，能把活干好就行。好像自从我大学时期读了垠神的这篇 《[谈程序的“通用性”][1]》 之后，写出的脚本和一次性轮子都是这种风格。

# 用法 #

这个脚本依赖 lxml 来生成 XML 文件，所以使用之前需要把这个依赖给装好。

```bash
pip install lxml
```

这个脚本的参数其实很少，-h 查看帮助，-i 指定输入文件，如果不指定就从 stdin 读取，-o 指定输出文件，如果不指定就输出到 stdout。

我一般这么用：

```
python duoshuo-migrator.py -i ~/Desktop/export.json  -o a.xml
```

如果程序执行的过程中发现有文章的标题为空，会往 stderr 中输出一些信息来提醒用户注意，比如这样：

> found article without title, id=1173938669371785301, link=http://www.jamespan.me/blog/2015/01/22/trick-of-paging-query/

# 最后 #

我对 lxml 库不是很熟悉，所以写生成 XML 那段代码还是颇费了一番功夫，写这种代码真是磨性子。

希望我顺手造的轮子能在你逃离多说拥抱 Disqus 的时候，帮你减少麻烦节省时间，也希望我的贡献让这个世界稍微变得美好了那么一点点~

# 参考 #

- [Importing your old comments to Disqus site](http://agiliq.com/blog/2015/01/importing-your-old-comments-to-disqus-site/)

[1]: http://www.yinwang.org/blog-cn/2013/04/13/generality/
