# rem
css、js对rem的使用。

一、css方法
    1.通过媒体查询@media动态设置html的字体大小来改变rem与px的比例
    html{
        font-size: 10px;
    }
    
    @media screen and (min-width: 320px) {
        html{
            font-size: 10px;
        }
    }
    @media screen and (min-width: 400px) {
        html{
            font-size: 12.5px;
        }
    }
    @media screen and (min-width: 480px) {
        html{
            font-size: 15px;
        }
    }
    @media screen and (min-width: 560px) {
        html{
            font-size: 17.5px;
        }
    }
    @media screen and (min-width: 640px) {
        html{
            font-size: 20px;
        }
    }
    2.通过vw单位设置html的字体大小
    html { font-size:0.13333333vw; }
    
二、js方法
    1.获取屏幕的宽度，通过addEventListener监听屏幕宽度大小，计算宽度与设计图宽度的比例来设置html的字体大小
    (function (doc, win) {
        var docEl = doc.documentElement,
            // 手机旋转事件,大部分手机浏览器都支持 onorientationchange 如果不支持，可以使用原始的 resize
            resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
            recalc = function () {
                //clientWidth: 获取对象可见内容的宽度，不包括滚动条，不包括边框
                var clientWidth = docEl.clientWidth;
                if (!clientWidth) return;
                docEl.style.fontSize = 20 * (clientWidth / 750) + 'px';
            };
        recalc();
        //判断是否支持监听事件 ，不支持则停止
        if (!doc.addEventListener) return;
        //注册翻转事件
        win.addEventListener(resizeEvt, recalc, false);
    })(document, window);

    2.淘宝弹性布局方案lib-flexible.js，通过dpr计算设置html的字体大小
    3.postcss-pxtorem
        Github: https://github.com/cuth/postcss-pxtorem
        安装：npm install postcss-pxtorem --save-dev
        配置：添加postcss.config.js文件
            module.exports = {
                plugins: {
                    'autoprefixer': {
                    browsers: ['Android >= 4.0', 'iOS >= 8']
                    },
                    'postcss-pxtorem': {
                    rootValue: 37.5,
                    propList: ['*']
                    }
                }
            }

VSCode配置：cssrem.rootFontSize
![Image](https://raw.githubusercontent.com/Gladysid/Images-blog/master/IE-box-pic.png)

