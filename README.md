# wangeditor-secondary-packaging-vue3.0
二次封装基于vue3.0的wangeditor，简洁实用，无需安装wangeditor插件包，引入子组件直接使用。


### 本组件基于Vue3.0 对wangeditor进行二次封装 ，目的是为了实现更灵活自由的使用，不被插件包版本限制，用户无需安装wangeditor。

```
```

### 使用方法：

将代码下载拷贝到 components文件下
引入：
```
import wangEditor from '@/components/wangeditor/index.vue' 
```
注册：
```
components:{wangEditor},
```
使用：
```
<wangEditor></wangEditor>
```
### 即可看到效果 （自带代码高亮显示）

### 参数配置：
设置html：  `:Editorhtml`

设置编辑器高度：  `:EditorHeight`

设置编辑器层级：  `:EditorZindex`

设置上传图片url：  `:EditorImgUrl`

设置上传视频url：  `:EditorVideoUrl`

<blockquote>
注意：本组件默认设置上传文件(图片)名为：file

####服务器返回格式要求：
```
  接口要返回 application/json 格式，格式要求如下：
  {
    // errno 即错误代码，0 表示没有错误。
    //       如果有错误，errno != 0，可通过下文中的监听函数 fail 拿到该错误码进行自定义处理
    "errno": 0,

    // data 是一个数组，返回图片Object，Object中包含需要包含url、alt和href三个属性,它们分别代表图片地址、图片文字说明和跳转链接,alt和href属性是可选的，可以不设置或设置为空字符串,需要注意的是url是一定要填的。
    "data": [
        {
            url: "图片地址",
            alt: "图片文字说明",
            href: "跳转链接"
        },
        {
            url: "图片地址1",
            alt: "图片文字说明1",
            href: "跳转链接1"
        },
        "……"
    ]
}
```

</blockquote>

### 回调函数
获取html：  `v-on:EditorValueFn`  回调带有一个参数（输出的html）

上传图片回调函数：  `v-on:getWangEditorimg`  回调带有一个参数（服务器返回的url）

上传视频回调函数：  `v-on:getWangEditorvideo`  回调带有一个参数（服务器返回的url）

#### 示例：
```
<wangeditor :Editorhtml="Editorhtml" v-on:EditorValueFn="EditorValueFn"></wangeditor>
```

<blockquote>需要注意的是：从编辑器中获取的 html 代码是不包含任何样式的纯 html，如果显示的时候需要对其中的 table code blockquote
等标签进行自定义样式（这样既可实现多皮肤功能）请引入插件中的 /css/tab.css 文件。<br>
文件包中含有dome文件，刚开始不知道 怎么用可以先看看dome文件里面的使用方法。<br>
如果有更好的封装方式 欢迎 ForK

</blockquote>

