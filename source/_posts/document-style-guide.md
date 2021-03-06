中文技术文档的写作规范

很多人说，不知道怎么写文档，都是凭着感觉写。

网上也很少有资料，教你写文档。这已经影响了中文软件的发展。

英语世界里，文档非常受重视，许多公司和组织都有自己的文档规范，清楚地规定写作要求，比如微软、MailChimp、Apple、Yahoo、docker、Struts 等等（维基百科有一份完整的清单）。中文的也有不少，但都不令人满意，要么太简单，要么不太适用。

我就动手，参考上面的规范，也结合自己的实践，总结了一份简单的《中文技术文档的写作规范》。

  1. [标题](https://github.com/ruanyf/document-style-guide/blob/master/docs/title.md)
  2. [文本](https://github.com/ruanyf/document-style-guide/blob/master/docs/text.md)
  3. [段落](https://github.com/ruanyf/document-style-guide/blob/master/docs/paragraph.md)
  4. [数值](https://github.com/ruanyf/document-style-guide/blob/master/docs/number.md)
  5. [标点符号](https://github.com/ruanyf/document-style-guide/blob/master/docs/marks.md)
  6. [章节结构](https://github.com/ruanyf/document-style-guide/blob/master/docs/structure.md)

我希望，这样可以抛砖引玉，让更多人重视文档，进而真正出现大家普遍接受的文档规范。

下面是关于写作风格的一个片段。欢迎提交 Issue 和 PR 补充。

=================================

## 写作风格
（摘自《中文技术文档的写作规范》）

如果使用了被动语态，应考虑更改为主动语态。

```
错误：假如此软件尚未被安装，

正确：假如尚未安装这个软件，
```

不使用非正式的语言风格。

```
错误：Lady Gaga 的演唱会真是酷毙了，从没看过这么给力的表演！！！

正确：无法参加本次活动，我深感遗憾。
```

用对"的"、"地"、"得"。

```
她露出了开心的笑容。
（形容词＋的＋名词）

她开心地笑了。
（副词＋地＋动词）

她笑得很开心。
（动词＋得＋副词）
```

使用代词时（比如"其"、"该"、"此"、"这"等词），必须明确指代的内容，保证只有一个含义。

```
错误：从管理系统可以监视中继系统和受其直接控制的分配系统。

正确：从管理系统可以监视两个系统：中继系统和受中继系统直接控制的分配系统。
```

名词前不要使用过多的形式词。

```
错误：此设备的使用必须在接受过本公司举办的正式的设备培训的技师的指导下进行。

正确：此设备必须在技师的指导下使用，且指导技师必须接受过由本公司举办的正式设备培训。
```

句子的长度尽量保持在20个字以内；20～29个字的句子，可以接受；39～39个字的句子，语义必须明确，才能接受；多于40个字的句子，在任何情况下都不能接受。

```
错误：本产品适用于从由一台服务器进行动作控制的单一节点结构到由多台服务器进行动作控制的并行处理程序结构等多种体系结构。

正确：本产品适用于多种体系结构。无论是由一台服务器（单一节点结构），还是由多台服务器（并行处理结构）进行动作控制，均可以使用本产品。
```

同样一个意思，尽量使用肯定句表达，不使用否定句表达。

```
错误：请确认没有接通装置的电源。

正确：请确认装置的电源已关闭。
```

避免使用双重否定句。

```
错误：没有删除权限的用户，不能删除此文件。

正确：用户必须拥有删除权限，才能删除此文件。
```

（正文完）