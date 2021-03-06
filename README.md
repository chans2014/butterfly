# Butterfly

Butterfly是完整的表单解决方案，自带表单验证、数据层、多表单主题支持和丰富的表单ui。

- 版本：1.4（基于kissy1.2）
- 作者：明河、紫英、张挺、牧云、易敛、飞绿、伯方
- <a href="http://butterfly.36ria.com/1.4/demo.html" target="_blank">Butterfly教程</a>

<img src="http://www.36ria.com/wp-content/uploads/2012/11/butterfly.png" />

 ## 包配置

```javascript
        KISSY.config({
            packages:[ {
                name:"gallery",
                path:"http://a.tbcdn.cn/s/kissy/",
                charset:"utf-8"
            } ]
        });
```

（PS:kissy1.3不再需要配置gallery包路径。）

## 目前可以使用的表单UI组件

### Uploader

 异步文件上传组件，支持ajax、iframe、flash三种上传方案,由明河（剑平）、紫英、飞绿完成，请勿使用v1.0和v1.1的代码。

 <img alt="uploader" src="http://www.36ria.com/wp-content/uploads/2012/05/uploader.png">

### Limiter

 字数统计组件，支持对kissy的富编辑器editor的统计，由明河（剑平）完成。

 <img alt="uploader" src="http://www.36ria.com/wp-content/uploads/2012/05/limiter.png">

### SpinBox

 数字增减器，由易敛完成。

 <img src="http://www.36ria.com/wp-content/uploads/2012/05/splinBox.png">

### Auth

 新的表单验证，由张挺完成。

 <img alt="uploader" src="http://www.36ria.com/wp-content/uploads/2012/05/kf-auth.png">

### Checkbox

 模拟多选框，用于表单美化，由伯方完成。

 <img alt="uploader" src="http://www.36ria.com/wp-content/uploads/2012/05/checkbox.png">

### Radio

 模拟单选框，用于表单美化，由伯方完成。

 <img alt="uploader" src="http://www.36ria.com/wp-content/uploads/2012/05/radio.png">

## 组件变更

### V1.4.0 change

    [!] multiple默认为false，禁用多选
    [!] 默认上传方式改成["ajax","iframe"]
    [-] 去掉data-config配置支持
    [-] 去掉不使用主题情况支持
    [+] 新增RenderUploader，ImageUploader和FileUploader继承于RenderUploader
    [!] 修正_errorHandler报错的bug（daogouUploader主题）
    [!] 去掉theme.js状态层的log提示
    [!] 将auth模块移到plugins下
    [!] singleImageUploader当已经有图片存在时替换图片
    [!] singleImageUploader去掉max限制
    [!] 重构UrlsInput，去掉create方法，不会自动创建urlsInput
    [+] uploader增加queue的add和remove事件

### V1.3.0 change

#### [+] 新增Butterfly
#### [+] 新增Select
#### [+] 新增List
#### Auth

    [+] #34消息采用更简单属性配置方式
    [+] #37可以通过msg-wrapper来配置消息层容器
    [+] 自定义规则可以传送验证配置值
    [+] 增加监听change事件验证select
    [!] add方法返回Field实例
    [!] 第一个参数可以为空
    [!] #35修复消息层显示后无法隐藏的bug
    [+] 新增getFieldAttrRules方法
    [+] 新增getName方法
    [+] 新增mergeConfig方法
    [+] Field新增rules属性

#### Limiter

    [+] #30 增加isCut参数，超过最大允许字数，不允许输入
    [+] #29 增加isEn参数，中英文情况的字数统计的处理

#### Uploader

    [+] 新增ImageUploader专用图片上传组件
    [+] #31 restore方法重构
    [+] ImageUploader可以使用优化的伪属性传参方式
    [+] Uploader新增action参数，用于配置服务器端路径
    [+] 新增filter参数，用于手动过滤服务器端不合法数据
    [+] 新增refundUploader主题
    [+] 新增daogou文件上传主题
    [+] 新增singleImageUploader主题
    [+] 新增testRequired
    [+] 自动将unicode转成中文
    [+] 可以直接通过uploader的实例，来获取验证配置
    [+] 给uploader增加testMax和testRequired方法
    [+] #25可以通过data-valid来配置验证消息
    [!] 1.2的imageUploader主题变成loveUploader
    [!] 重构imageUploader主题，让主题更具通用性
    [!] 优化图片预览插件，支持多选图片预览（IE下不支持图片预览）
    [!] 修正flash下返回的服务器端编码乱码的问题
    [!] 验证规则require改成required，为了和html中的required属性保持统一
    [!] auth的error事件对象增加index
    [!] 不再建议操作auth的实例
    [!] #27修正imageUploader主题打印出错消息时，不隐藏mask层
    [!] 修正当没有设置max时，脚本设置无效的问题
    [-] Uploader弃用restoreHook
    [-] Auth弃用require
    [-] Uploader弃用serverConfig
    [-] Uploader弃用restore事件
    [!] 修正iframe remove form时的报错问题
    [!] 修正data传递失败的问题

#### Radio

    [+] 监听原生click事件，触发模拟radio的选中

#### Checkbox

    [+] 新增change方法
    [+] 新增isChecked方法
    [-] 去掉fire原生多选框的click事件

### V1.2.7 change

Uploader

    修正最大文件字节数统计错误的bug
    #92 增加restore事件
    #93 当达到最大允许上传数时，删除一张图片，再传一张，testMax验证失效，没有禁用按钮

V1.2.6 change

Uploader

    error事件数据增加status和file
    优化imageUploader主题
    前端验证，事件参数增加result:{},与uploader的error事件保持一致
    #85 uploader增加data属性，用于动态配置post到服务器端的数据
    #84 uploader增加multipleLen参数控制多选图片最大张数
    #69 修正flash上传隐藏按钮后无法上传
    #75 修正restore数据时不触发auth验证的bug
    #76 auth的事件集成到uploader的error事件中
    #80 修正在chrome19下文件多选时首次可以多选，之后就只能单选的bug
    #81 修正开启拖拽后，禁用按钮时，没有移除拖拽区域的bug
    #82 修正默认主题状态层有进度条时删除入口跑到第二行的bug

Radio

    美化样式
    #78 当label不存在时，只初始化一个radio

Checkbox

    美化样式
    当label不存在时，只初始化一个checkbox
    早期版本（主要是uploader的更新）

### V1.2.3 change

    #69 修正flash上传隐藏按钮后无法上传
    修正flash文件无法过滤
    imageUploader主题增加isMaxHideBtn配置

### V1.2.2 change

    #68 修正iframe上传按钮在IE下无法点击的bug
    #67 修正flash上传，安全漏洞问题的bug
    #66 修正restore方法时没有触发auth的max验证的bug
    post上传方式到服务器端(type)
    解析json前先清空空格
    demo中心优化

### V1.2.1 change

    #57 修正小版本firefox出现按钮无法点击的bug
    #58 修正flash上传存在无法找到文件域的bug
    #59 修正初始按钮过大
    #35 修正鼠标手型bug
    #60 修正iframe上传方式在不存在data的情况下会报错的bug
    #61 修正queueTarget不存在时会有bug的bug
    #61 uploader增加swfSize参数，用于强制设置flash大小
    #65 flash多个实例的情况下会出现冲突的bug
    #64 图片上传进度条存在bug

### V1.2.0 change

    #43 修正取消操作无用的bug
    #44 修正IE6/IE7会报缺少）的错误的bug
    #49 修正IE6下可点击区域过小无法调整的bug
    #51 修正进度条bug
    图片预览在多选下存在bug，先予以禁用
    #26 type:auto，改成等价于["ajax","flash","iframe"]，除非是特别需求，不推荐修改type
    #27 IE下优先使用flash，解决多选问题
    #50 增加themeConfig、authConfig参数
    #50 button的配置集成到uploader/base.js，uploader增加multiple和disabled二个属性， 非特殊需求请勿直接修改button实例的属性，去掉data-button-config支持
    #52 修正type设置有flash，却不实例化flash按钮的bug
    优化主题样式加载时机（之前按钮的大小设置有问题）
Filedrop增加isSupport属性

### V1.1.4 change

    修正进度换算bug
    修正不加载插件不执行回调bug
    修正不使用主题的情况下，监听init事件无效的bug
    修正多个iframe上传的bug
    修正imageUploader主题删除图片后无法显示按钮的bug
    修正不使用插件，对应插件没做容错处理的bug

### V1.1.3 change

    修正restore方法无法处理服务器端的bug
    支持不使用内置主题的情况，设置theme:''
    queue初始化过程移到RenderUploader
    增加个不使用内置主题的demo
    修正ajax上传，修改了传给服务器端的参数,serverConfig，但上传时依旧post旧的数据
    淘宝二手市场主题重新可用
    去掉isUseCss多余的判断

### V1.1.2 change

    优化Queue类，Queue不再包含dom操作
    Queue配置项，增加fnAdd（添加文件后执行的回调函数）
    删除与DOM相关的配置项和属性
    Queue的dom操作移到theme处理，用户可以自由覆盖控制li元素的显隐，以及是否输出DOM结构
    Theme增加plugins参数，组件自动加载插件
    修正主题引用路径的bug
    默认开启文件多选（多选bug已经修复）
    优化默认主题的样式
    修正imageUploader，默认有数据的情况下统计失败的问题

### V1.1 change

    重构主题基类，让主题制作更简单
    去掉难以理解的Status类，状态变更集成到Theme
    增加Theme主题基类，主题不再继承DefaultTheme，导致会加载多余样式
    新增imageUploader主题，先去除不可用的grayQueue和lineQueue主题
    增加拖拽上传插件
    增加拖拽主题
    修正多处兼容性bug
    主题路径，如果使用的是组件内置主题，只要传递主题名就好
    修正ajax多选上传，只上传一个图片的bug
    优化拖拽上传插件，支持点击上传
    修正验证失败依旧上传的bug
    重写restore方法，可以从页面抓取文件数据，而不是从urlsInput
    修正图片预览报错bug
