# RequireJS使用规范

RequireJS的使用约定和注意事项


## 模块定义

1. 固定给requirejs调用的模块均以define定义
2. 公共使用的代码库（如：插件等），则最好写成UMD的形式
3. 写成UMD形式的代码意味着非强制依赖`requirejs`，所以不得在使用`require`来延迟加载

#### 影响

写成UMD不强制依赖requirejs

#### 例子

jquery插件模块
```js
// 不推荐
define(['jquery'] ,function($){
    var plusName = 'test';
    $.fn[plusName] =function(){
        // todo
    };
});

// 推荐
(function(factory){
    if ( typeof define === "function" ) {
        define(['jquery'] ,factory);
    }else{
        factory(jQuery);
    }
}(function($){
    var plusName = 'test';
    $.fn[plusName] =function(){
        // todo
    };
}));
```

错误写法
```js
(function(factory){
    if ( typeof define === "function" ) {
        define(['jquery'] ,factory);
    }else{
        factory(jQuery);
    }
}(function($){
    var plusName = 'test';
    $.fn[plusName] =function(){
        // todo
        $(selector).click(function(){
            // 此处有误：强制依赖require
            require('other/script');
        });
    };
}));
```

#### 重要性

推荐


## paths配置

1. 在使用中，如非频繁广泛使用的模块（或第三方模块），最好不要简化模块名称，即定义在`paths`中。
2. 模块路径都是绝对的，所以不得使用`/`、`./`等开头，`http`的除外

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

// 不推荐
require.config({
    // other...
});
require(['./plugin/myModule' ,'/lib/myModule'] ,function(a ,b){
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