#### 关键帧动画

`animation-timing-function`动画的执行时序效果。

`steps(步数)`，步进时序方法。

步数必须是正数，将动画分为`步数`对应的段数。

1s，5步，动画的每一步就需要200ms。

使用`steps()`时，属性不是连续不断滑入的（没有过渡效果，直接到）

#### 简写格式

`animation:name duration timing-function delay iteration-count direction`

* name，动画名
* duration，持续时间，0s。
* timing-function，效果。ease，慢-》快-》慢。
* delay，延迟，0s。
* iteration-count，播放次数，1次。
* direction，normal（0~100%）。

#### 布局方案

1. 左侧固定右侧自适应（两列布局）

    * 方法一：absolute

        ```html
        <!DOCTYPE html>
        <html>
            <head>
                <style>
                    html,body{
                        margin:0;
                        height:100%;
                    }
                    #content{
                        position: relative;
                        width:100%;
                        height:100%;
                        background-color: lightcoral;
                    }
                    #left{
                        width:300px;
                        height:100%;
                        background-color:lightseagreen;
                    }
                    #right{
                        /* 
                        
                        容纳块宽度+padding = left + margin-left + border-left + padding-left + width + padding-right + border-right + margin-right + right
                        850+0 = 0 + 300 + 0 + 0 + x + 0 + 0 + 0 + 0
                        850=300+x
                        x = 850-300
                         */
                        position:absolute;
                        top:0;
                        bottom:0;
                        right:0;
                        left:0;
                        margin-left:300px;
                        background-color:lightskyblue;
                    }
                </style>
            </head>
            <body>
                <div id="content">
                    <div id="left">左边</div>
                    <div id="right">右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边右边</div>
                </div>
            </body>
        </html>
        ```

    * 方法二：float方法

        ```html
        <!DOCTYPE html>
        <html>
        
        <head>
            <style>
                html,
                body {
                    margin: 0;
                    height: 100%;
                }
        
                #content {
                    width: 100%;
                    height: 100%;
                    background-color: pink;
                }
        
                #right {
                    float: left;
                    width: 100%;
                    height: 100%;
                    background-color: royalblue;
                }
                #right #c{
                    /*容纳块宽度=margin-left 300 + border-left 0 + padding-left 0 + width(auto) + padding-right 0 + border-right 0 + margin-right 0*/
                    /*容纳块宽度=300 + auto*/
                    /* auto = 容纳块元素 - 300 */
                    margin-left:300px;
                    height:100%;
                    background-color: tomato;
                }
        
                #left {
                    /* 浮动元素必须尽可能高的放置 */
                    margin-left:-100%;
                    float: left;
                    width: 300px;
                    height: 100%;
                    background-color: springgreen;
                }
            </style>
        </head>
        
        <body>
            <div id="content">
                <div id="right">
                    <div id="c">!呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵呵</div>
                </div>
                <div id="left">
                    左边
                </div>
            </div>
        </body>
        
        </html>
        ```

2. 三列布局

    双飞翼布局和圣杯布局都需要用到上面的内容，但是他们的区别在于被遮挡住的内容怎么被显示出来。

    * 双飞翼布局被遮挡的内容是通过里面的`#c`然后通过容纳块公式（设置margin-left和margin-right）让其显示出来。

    * 双飞翼布局

        ```html
        <!DOCTYPE html>
        <html>
        
        <head>
            <style>
                html,
                body {
                    margin: 0;
                    height: 100%;
                }
                #content{
                    width:100%;
                    height:100%;
                    background-color: tomato;
                }
                #middle{
                    float:left;
                    width:100%;
                    height:100%;
                    background-color:yellowgreen;
                }
                #middle #c{
                    margin-left:200px;
                    margin-right:200px;
                    height:100%;
                    background-color:lawngreen;
                }
                #left{
                    /* 使用margin-left:-100%拉倒最左边 */
                    margin-left:-100%;
                    float:left;
                    width:200px;
                    height:100%;
                    background-color: gold;
                }
                #right{
                    margin-left:-200px;
                    float:left;
                    width:200px;
                    height:100%;
                    background-color: hotpink;
                }
            </style>
        </head>
        
        <body>
            <div id="content">
                <div id="middle">
                    <div id="c">!这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容这里是中间的内容</div>
                </div>
                <div id="left">左边</div>
                <div id="right">右边</div>
            </div>
        </body>
        
        </html>
        ```

    * 圣杯布局

        



