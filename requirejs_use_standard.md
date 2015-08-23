# RequireJS使用规范

RequireJS的使用约定和注意事项


## paths配置

在使用中，如非频繁广泛使用的模块（或第三方模块），最好不要简化模块名称，即定义在`paths`中。

#### 影响

因为如果整个项目打包，不知道其他协作的同学有没有定义在`paths`，这样可能会存在冲突。

#### 例子

```js
// 不推荐
require.config({
    // other...
    paths:{
        myModule1: 'plugin/myModule',
        myModule2: 'lib/myModule'
    }
});
require(['myModule1' ,'myModule2'] ,function(a ,b){
    // todo
});

// 推荐
require.config({
    // other...
});
require(['plugin/myModule' ,'lib/myModule'] ,function(a ,b){
    // todo
});
```

#### 重要性

必须
