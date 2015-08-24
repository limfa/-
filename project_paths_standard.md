# 前端文件目录命名规范

路径的命名与文件的放置


## 目录结构

以资源类型总分，再以项目模块二分

```
// 源码目录
source
    // 脚本
  --script
    // 样式
  --style
    // 图片
  --image
    // 字体
  --font
    // flash
  --flash
    // 音频
  --audio
    // 视频
  --video
    // 其它
  --other

// 发布目录
public
```

## 文件命名

所有文件都统一以**小写加`-`**的命名方式命名

#### 例子

```
不推荐
MyScript.js
myCamelCaseName.css
i_love_underscores.html
1001-scripts.js
my-file-min.css

推荐
my-script.js
my-camel-case-name.css
i-love-underscores.html
thousand-and-one-scripts.js
my-file.min.css
```

### 重要性

必须