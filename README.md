Markdown-Extra-Customize-Attribute
==================================

如果要为 Markdown 的一段文字增加样式属性，就必须写成 HTML 代码:

	<p class="bg-blue" markdown="1">*弗朗茨·李斯特（Franz Liszt）*: 著名匈牙利作曲家、钢琴家、指挥家。</p>

但 Markdown 解析器通常不会对 HTML 代码中的内容再进行解析，因此 *弗朗茨·李斯特（Franz Liszt）*并不会解析成 <em>弗朗茨·李斯特（Franz Liszt）</em>，需声明 `markdown="1"` （但有一些解析器还是不支持）。

如何在不改变 Markdown 语法，也不影响阅读和迁移的情况下，方便地来自定义样式属性？

## 我的想法

我的想法是利用 HTML 的注释 <!--注释--> 来自定义样式，如：

	<!--.bg-blue-->

	*弗朗茨·李斯特（Franz Liszt）*: 著名匈牙利作曲家、钢琴家、指挥家。

有了这行注释，我们就知道要将接下来的一段内容一起解析为如下 HTML ：

	<p class="bg-blue">
	    <em>弗朗茨·李斯特（Franz Liszt）</em>: 著名匈牙利作曲家、钢琴家、指挥家。
	</p>

也可以扩展成多段落：

	<!--begin.bg-blue-->

	*弗朗茨·李斯特（Franz Liszt），著名匈牙利作曲家、钢琴家、指挥家。

	《钟》（意大利语：La campanella），是弗朗茨·李斯特创作的《帕格尼尼大练习曲》6首中第3首的钢琴独奏曲。

	<!--end.bg-blue-->

## WordPress插件

下载并解压至 wp-content/plugins/ 中，在后台激活插件即可。

插件没有提供CSS，需自行定义。
