# CSS编码规范

CSS相关文件书写风格及注意事项规范

## 命名

一律小写，必要时使用 `-` 连接符

#### 影响

（无）

#### 例子

```css
/*不推荐*/
.gameHeader{}
/*推荐*/
.game-header{}
```

#### 重要性

必须


## 选择器

1. 尽量使用**类选择器**，尽量不要使用**id选择器** 、**标签选择器**等
2. 尽量使用**单一选择器**
3. 选择器层级最好不要超过*3*层

#### 影响

1. 尽量不使用对全局影响的选择器，像单独的标签选择器
2. 选择器层级太多会影响浏览器对css解析的性能

#### 例子

```css
/*不推荐*/
#foo-header {}
div a{}
div:first-child {}
/*推荐*/
.foo-header {}
```

```css
/*不推荐*/
.foo-header .foo-header-nav
/*推荐*/
.foo-header-nav
```

#### 重要性

必须


## 属性

尽量简写属性

#### 影响

（无）

#### 例子

```css
//不推荐
.foo{
    padding-top: 2px; 
    padding-bottom: 4px; 
    padding-left: 3px; 
    font-family: 'microsoft yahei';
    font-size: 12px;
    font-weight: normal;
    line-height: 2em;
}    
//推荐
.foo{
    padding: 2px 0 4px 3px;
    font: normal 12px/2em 'microsoft yahei';
}
```

#### 重要性

推荐
