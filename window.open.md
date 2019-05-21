``` javascript
// 异步使用window.open在部分浏览器会被拦截
$.ajax('xxx', (data) => {
    window.open(data.url)
});

// 解决办法,同步弹出一个空窗口,异步请求后重定向
var newWin = window.open('');
$.ajax('xxx', (data) => {
    newWin.location.href = data.url;
});

// 给window.open窗口添加新DOM,ie会报错
var newWin = window.open('');
var loadingImg = new Image();
loadingImg.src = 'xxx';
newWin.document.body.appendChild(loadingImg);

// 解决办法,需要使用新窗口对象的document创建
var newWin = window.open('');
var loadingImg = new newWin.Image();
loadingImg.src = 'xxx';
newWin.document.body.appendChild(loadingImg);
```