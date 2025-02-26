# Balloon

-   category: Components
-   family: Feedback
-   chinese: 气泡提示
-   type: 弹层

---

气泡组件。

## 何时使用

-   当用户与被说明对象（文字，图片，输入框等）发生交互行为的action开始时, 即刻跟随动作出现一种辅助或帮助的提示信息。
-   其中Balloon.Tooltip是简化版本，主要用于hover时显示简单文案

### `v2` 版本更新指示

1.25 版本增加 v2 支持开启新版本弹，功能如下

-   底层更换 v2 版本弹窗组件，可根据空间动态调整位置，解决页面滚动造成弹窗脱离的问题
-   默认边缘对齐，增加 `arrowPointToCenter` 开启后箭头指向中间

## 如何使用

-   对于trigger是自定义的React Component的情况，自定义的React Component 需要透传onMouseEnter/onMouseLeave/onClick 事件。
-   若要使用无障碍的气泡提示，请传入id。推荐简单提示使用`<Tooltip>`、复杂交互使用`<Balloon triggerType="click">` 。 triggerType="focus"作为辅助状态用于组件内部，请用户不要直接使用此值。

## API

### Balloon

| 参数                 | 说明                                                                                                                                                                                                                                                    | 类型             | 默认值                                                            | 版本支持 |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | -------------------------------------------------------------- | ---- |
| children           | 浮层的内容                                                                                                                                                                                                                                                 | any            | -                                                              |      |
| type               | 样式类型<br/><br/>**可选值**:<br/>'normal', 'primary'                                                                                                                                                                                                        | Enum           | 'normal'                                                       |      |
| title              | 标题                                                                                                                                                                                                                                                    | ReactNode      | -                                                              | 1.23 |
| visible            | 弹层当前显示的状态                                                                                                                                                                                                                                             | Boolean        | -                                                              |      |
| defaultVisible     | 弹层默认显示的状态                                                                                                                                                                                                                                             | Boolean        | false                                                          |      |
| onVisibleChange    | 弹层在显示和隐藏触发的事件<br/><br/>**签名**:<br/>Function(visible: Boolean, type: String) => void<br/>**参数**:<br/>_visible_: {Boolean} 弹层是否隐藏和显示<br/>_type_: {String} 触发弹层显示或隐藏的来源， closeClick 表示由自带的关闭按钮触发； fromTrigger 表示由trigger的点击触发； docClick 表示由document的点击触发 | Function       | func.noop                                                      |      |
| v2                 | 开启 v2 版本                                                                                                                                                                                                                                              | Boolean        | -                                                              | 1.25 |
| arrowPointToCenter | [v2] 箭头是否指向目标元素的中心                                                                                                                                                                                                                                    | Boolean        | false                                                          | 1.25 |
| closable           | 是否显示关闭按钮                                                                                                                                                                                                                                              | Boolean        | true                                                           |      |
| align              | 弹出层位置<br/><br/>**可选值**:<br/>'t'(上)<br/>'r'(右)<br/>'b'(下)<br/>'l'(左)<br/>'tl'(上左)<br/>'tr'(上右)<br/>'bl'(下左)<br/>'br'(下右)<br/>'lt'(左上)<br/>'lb'(左下)<br/>'rt'(右上)<br/>'rb'(右下)                                                                           | Enum           | 'b'                                                            |      |
| offset             | 弹层相对于trigger的定位的微调, 接收数组[hoz, ver], 表示弹层在 left / top 上的增量<br/>e.g. [100, 100] 表示往右(RTL 模式下是往左) 、下分布偏移100px                                                                                                                                            | Array          | [0, 0]                                                         |      |
| trigger            | 触发元素                                                                                                                                                                                                                                                  | any            | &lt;span />                                                    |      |
| triggerType        | 触发行为<br/>鼠标悬浮, 鼠标点击('hover','click')或者它们组成的数组，如 ['hover', 'click'], 强烈不建议使用'focus'，若弹窗内容有复杂交互请使用click                                                                                                                                                 | String/Array   | 'hover'                                                        |      |
| onClose            | 任何visible为false时会触发的事件<br/><br/>**签名**:<br/>Function() => void                                                                                                                                                                                        | Function       | func.noop                                                      |      |
| autoAdjust         | [v2] 是否进行自动位置调整，默认自动开启。                                                                                                                                                                                                                               | Boolean        | -                                                              | 1.25 |
| delay              | 弹层在触发以后的延时显示, 单位毫秒 ms                                                                                                                                                                                                                                 | Number         | -                                                              |      |
| afterClose         | 浮层关闭后触发的事件, 如果有动画，则在动画结束后触发<br/><br/>**签名**:<br/>Function() => void                                                                                                                                                                                   | Function       | func.noop                                                      |      |
| autoFocus          | 弹层出现后是否自动focus到内部第一个元素                                                                                                                                                                                                                                | Boolean        | true                                                           |      |
| safeNode           | 安全节点:对于triggetType为click的浮层,会在点击除了浮层外的其它区域时关闭浮层.safeNode用于添加不触发关闭的节点, 值可以是dom节点的id或者是节点的dom对象                                                                                                                                                         | String         | undefined                                                      |      |
| safeId             | 用来指定safeNode节点的id，和safeNode配合使用                                                                                                                                                                                                                       | String         | null                                                           |      |
| animation          | 配置动画的播放方式，格式是{in: '', out: ''}， 常用的动画class请查看Animate组件文档                                                                                                                                                                                              | Object/Boolean | {     in: 'zoomIn zoomInBig',     out: 'zoomOut zoomOutBig', } |      |
| cache              | 弹层的dom节点关闭时是否删除                                                                                                                                                                                                                                       | Boolean        | false                                                          |      |
| popupContainer     | 指定浮层渲染的父节点, 可以为节点id的字符串，也可以返回节点的函数。                                                                                                                                                                                                                   | any            | -                                                              |      |
| popupStyle         | 弹层组件style，透传给Popup                                                                                                                                                                                                                                    | Object         | {}                                                             |      |
| popupClassName     | 弹层组件className，透传给Popup                                                                                                                                                                                                                                | String         | ''                                                             |      |
| popupProps         | 弹层组件属性，透传给Popup                                                                                                                                                                                                                                       | Object         | {}                                                             |      |
| followTrigger      | 是否跟随滚动                                                                                                                                                                                                                                                | Boolean        | -                                                              |      |
| id                 | 弹层id, 传入值才会支持无障碍                                                                                                                                                                                                                                      | String         | -                                                              |      |

### Balloon.Tooltip

| 参数                 | 说明                                                                                                                                                                          | 类型           | 默认值         |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ----------- |
| children           | tooltip的内容                                                                                                                                                                  | any          | -           |
| align              | 弹出层位置<br/><br/>**可选值**:<br/>'t'(上)<br/>'r'(右)<br/>'b'(下)<br/>'l'(左)<br/>'tl'(上左)<br/>'tr'(上右)<br/>'bl'(下左)<br/>'br'(下右)<br/>'lt'(左上)<br/>'lb'(左下)<br/>'rt'(右上)<br/>'rb'(右下) | Enum         | 'b'         |
| trigger            | 触发元素                                                                                                                                                                        | any          | &lt;span /> |
| triggerType        | 触发行为<br/>鼠标悬浮,  鼠标点击('hover', 'click')或者它们组成的数组，如 ['hover', 'click'], 强烈不建议使用'focus'，若有复杂交互，推荐使用triggerType为click的Balloon组件                                                 | String/Array | 'hover'     |
| popupStyle         | 弹层组件style，透传给Popup                                                                                                                                                          | Object       | -           |
| popupClassName     | 弹层组件className，透传给Popup                                                                                                                                                      | String       | -           |
| popupProps         | 弹层组件属性，透传给Popup                                                                                                                                                             | Object       | -           |
| pure               | 是否pure render                                                                                                                                                               | Boolean      | -           |
| popupContainer     | 指定浮层渲染的父节点, 可以为节点id的字符串，也可以返回节点的函数。                                                                                                                                         | any          | -           |
| followTrigger      | 是否跟随滚动                                                                                                                                                                      | Boolean      | -           |
| id                 | 弹层id, 传入值才会支持无障碍                                                                                                                                                            | String       | -           |
| delay              | 如果需要让 Tooltip 内容可被点击，可以设置这个参数，例如 100                                                                                                                                        | Number       | 50          |
| v2                 | 开启 v2 版本                                                                                                                                                                    | Boolean      | -           |
| arrowPointToCenter | [v2] 箭头是否指向目标元素的中心                                                                                                                                                          | Boolean      | false       |

## 无障碍键盘操作指南

| 按键    | 说明                              |
| :---- | :------------------------------ |
| SPACE | 当`triggerType=‘click’`时，点击会弹出提示 |
| Enter | 当`triggerType=‘click’`时，点击会弹出提示 |
