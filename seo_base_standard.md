# 前端SEO基础规范

需要搜索引擎收录的页面都需要遵循此规范

## meta标签

1. `title`，标题
2. `keywords`，4、5个关键字
3. `description` ，描述

#### 影响

网站的基本信息，对网站seo很重要

#### 例子

```html
<title>标题</title>
<meta name="keywords" content="keyword1,keyword2,keyword3,keyword4" />
<meta name="description" content="网站描述" />
```

#### 重要性

必须


## 关键字标签

1. 唯一的`h1`标签
2. 内容的关键字按权重使用`strong`，`b`等

#### 影响

网站的主要内容信息，对网站seo很重要

#### 例子

```html
<h1>标题</h1>
<p>内容...<strong>关键字1</strong></p>
<p>内容...<b>关键字2</b></p>
```

#### 重要性

必须


## img标签

与内容相关图片需要加上`alt`、`title`属性描述图片

#### 影响

网站内容相关的图片信息，对网站seo很重要

#### 例子

```html
<img src="http://xxx" alt="图片描述" title="图片描述">
```

#### 重要性

必须


## a标签

1. a标签只可包含内容文本或图片
2. 不考虑seo的链接添加`rel="nofollow"`属性值
3. 避免死链

#### 影响

1. 非文本的a标签，对爬虫识别不友好
2. `rel="nofollow"`可以提示爬虫不抓取
3. 死链会降低网站权重

#### 例子

（无）

#### 重要性

必须

