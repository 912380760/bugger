``` JS
// 不规范的写法,会初始化这个元素的style,在ie下会报错
element.style = 'background: red;width: 100px; height: 100px';

// 推荐使用element.style.attribute
element.style.background = 'red';
element.style.width = '100px';
element.style.height = '100px';

// 或添加一个style标签,给element添加class
const style = document.createElement('style'),
    className = 'className';
style.type = 'text/css'
style.innerHtml = `
.${className} {
    background: red;
    width: 100px;
    height: 100px;
}`;
document.head.appendChild(style);
element.classList.add(className);
```