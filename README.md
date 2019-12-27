# rem
css、js对rem的使用。

1.css方法
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
    
2.js方法

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
