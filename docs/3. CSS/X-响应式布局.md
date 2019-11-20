# 响应式布局

> css中的1px并不等于设备的1px [viewport深入理解](https://www.cnblogs.com/2050/p/3877280.html)


#### 响应式断点 (bootstrap, antd)
> [Responsive breakpoints](https://getbootstrap.com/docs/4.0/layout/overview/#responsive-breakpoints)
> [栅格 Grid](https://ant-design.gitee.io/components/grid-cn/#Col)


#### 桌面优先还是移动优先

在做响应式的时候我们一般有个原则叫做是移动优先还是pc优先，bootstrap采用的是移动优先，移动优先的特点是先考虑设计移动的样式，然后再设置断点一步步向大尺寸添砖加瓦增加样式，所以采用min-width（移动端的样式相对来说都比较简单，而pc相对来说要复杂点，所以这种顺序是样式由少到多，由简单到复杂的过程）。反过来如果你的业务是pc优先，那默认是pc的样式，兼容到移动的时候就是由大到小，所以采用max-width（这种方式后面的移动端需要重置覆盖默认pc上的很多样式，比较浪费）

移动优先
```css
/* Small devices (landscape phones, 576px and up) */
@media (min-width: 576px) { ... }

/* Medium devices (tablets, 768px and up) */
@media (min-width: 768px) { ... }

/* Large devices (desktops, 992px and up) */
@media (min-width: 992px) { ... }

/* Extra large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) { ... }

/* antd 扩展 xxl 设备 */
@media (min-width: 1600px) { ... }
```