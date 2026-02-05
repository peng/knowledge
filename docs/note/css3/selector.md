## CSS选择器整理

#### 基本选择器

| 选择器         | 名称           | 描述  |
| ------------- |:-------------:| :----- |
| *             | 通配选择器      | 选择文档中所有的HTML元素 |
| E             | 元素选择器      | 选择指定类型的HTML元素，例如：li、p等等 |
| #id           | ID 选择器      | 选择ID属性值为 “id” 的元素 |
| .class        | 类选择器       | 选择class属性值为 “class” 的一组元素 |
| selector1, selector2        | 群组选择器       | 将每一个选择器匹配的集合合并 |

#### 层次选择器

| 选择器         | 名称           | 描述  |
| ------------- |:-------------:| :-----|
| selector1 selector2  | 后代选择器(包含选择器) | 选择selector2所匹配的一组元素，且selector2是selector1的后代元素 |
| selector1 > selector2  | 子选择器 | 选择selector2所匹配的一组元素，且selector2是selector1的直接子元素 |
| selector1 + selector2  | 相邻兄弟选择器 | 选择selector2所匹配的元素，且selector2位于selector1的后面 |
| selector1 ~ selector2  | 通用选择器 | 选择selector2所匹配的一组元素，且该组元素位于selector1后面 |

#### 伪类选择器

##### 动态伪类选择器

| 选择器             | 名称                | 描述  |
| ------------------|:-------------------:| :-----|
| selector:link     | 连接伪类选择器   | 选择selector所匹配的元素，且该元素被定义了超链接并未被访问过，常用于a标签 |
| selector:visited  | 连接伪类选择器   | 选择selector所匹配的元素，且该元素被定义了超链接并已被访问过，常用于a标签 |
| selector:active   | 用户行为伪类选择器   | 选择selector所匹配的元素，且该元素被激活，常用于连接或按钮上 |
| selector:hover    | 用户行为伪类选择器   | 选择selector所匹配的元素，且用户鼠标停留在该元素上 |
| selector:focus    | 用户行为伪类选择器   | 选择selector所匹配的元素，且该元素获得焦点 |

##### 目标伪类选择器

| 选择器             | 名称                | 描述  |
| ------------------|:-------------------:| :-----|
| selector:target   | 目标伪类选择器   | 选择selector所匹配的元素，且该元素的ID值等于页面URL片段标识符(即#号后面的值)的值 |

##### 语言伪类选择器

| 选择器             | 名称                | 描述  |
| ------------------|:-------------------:| :-----|
| selector:lang(language)   | 语言伪类选择器   | 选择selector所匹配的元素，且该元素指定了值为 language 的 lang 属性，多用于多语言网站不同样式的处理上 |

##### UI元素状态伪类选择器

| 选择器             | 名称                | 描述  |
| ------------------|:-------------------:| :-----|
| selector:checked   | 选中状态伪类选择器   | 匹配选中的单选按钮/复选按钮 |
| selector:enabled   | 启用状态伪类选择器   | 选择selector所匹配的表单元素，其该元素为启用状态 |
| selector:disabled   | 禁用状态伪类选择器   | 选择selector所匹配的表单元素，其该元素为禁用状态 |

##### 结构伪类选择器

| 选择器                  | 描述                |
| -----------------------|:-------------------:|
| selector:first-child   | 选择selector所匹配的元素，且该元素是其父元素的第一个子元素(不算文本节点，也不区分元素类型)，等价于 selector:nth-child(1)   |
| selector:last-child    | 选择selector所匹配的元素，且该元素是其父元素的最后一个子元素(不算文本节点，也不区分元素类型)，等价于 selector:nth-last-child(1)   |
| selector:nth-child(n)  | 选择selector所匹配的元素，且该元素是其父元素的第n个子元素(不算文本节点，也不区分元素类型)，其中 n 的值可以使正数(1、2、3...)，也可以是关键字(even、odd)，也可以是公式(2n+1、2n-1...)，且 n 的起始值是1而不是0 |
| selector:nth-last-child(n)  | 选择selector所匹配的元素，且该元素是其父元素的倒数第n个子元素(不算文本节点，也不区分元素类型) |
| selector:first-of-type  | 选择selector所匹配的元素，且该元素是其父元素的第一个特定类型的子元素(不算文本节点，区分元素类型) |
| selector:last-of-type  | 选择selector所匹配的元素，且该元素是其父元素的最后一个特定类型的子元素(不算文本节点，区分元素类型) |
| selector:nth-of-type(n)  | 选择selector所匹配的元素，且该元素是其父元素的第n个特定类型的子元素(不算文本节点，区分元素类型) |
| selector:nth-last-of-type(n)  | 选择selector所匹配的元素，且该元素是其父元素的倒数第n个特定类型的子元素(不算文本节点，区分元素类型) |
| selector:only-child    | 选择selector所匹配的元素，且其父元素只有它一个子元素(不算文本节点，也不区分元素类型) |
| selector:only-of-type  | 选择selector所匹配的元素，且其父元素只有它一个特定类型的子元素(不算文本节点，区分元素类型) |
| selector:root          | 选择selector所匹配的元素所在文档的根元素，即html元素 |
| selector:empty         | 选择selector所匹配的元素，且该元素没有任何子元素(包括文本节点) |


##### 否定伪类选择器

| 选择器                  | 描述                |
| -----------------------|:-------------------:|
| selector1:not(selector2)   | 选择所有不包含selector2的selector1元素  |

#### 伪元素

| 选择器                  | 描述                |
| -----------------------|:-------------------:|
| selector::first-letter   | 选择文本块的第一个字母  |
| selector::first-line   | 选择文本块的第一行文本  |
| selector::before   | 用来为selector所匹配的元素的所有子元素前面插入内容，插入的内容不会成为DOM的一部分，但是依然可以设置样式  |
| selector::after   | 用来为selector所匹配的元素的所有子元素后面插入内容，插入的内容不会成为DOM的一部分，但是依然可以设置样式  |
| selector::selection   | 匹配被鼠标选中的文本  |

<p class="tip">双冒号代表伪元素，单冒号代表伪类</p>

#### 属性选择器

| 选择器                  | 描述                |
| -----------------|:-------------------:|
| selector[attr]   | 选择selector所匹配的元素，且该元素拥有attr属性。可以省略selector，表示匹配所有拥有attr属性的元素  |
| selector[attr=val]   | 选择selector所匹配的元素，且该元素拥有值为val的attr属性。可以省略selector，表示匹配所有拥有值为val的attr属性的元素  |
| selector[attr~=val]   | 选择selector所匹配的元素，且该元素attr属性值具有多个空格分隔的值，其中一个值等于val。可以省略selector|
| selector[attr*=val]   | 选择selector所匹配的元素，且该元素attr属性值的任意位置包含val。可以省略selector|
| selector[attr^=val]   | 选择selector所匹配的元素，且该元素attr属性值以val开头。可以省略selector|
| selector[attr$=val]   | 选择selector所匹配的元素，且该元素attr属性值以val结尾。可以省略selector|

除了上表中介绍的属性选择器之外，还有一个属性选择器没有写在其中，如下：

```css
/* 选择selector所匹配的元素，且该元素拥有值以val或val-开头的attr属性，可以省略selector */
selector[attr|=val] {

}
```

你可能会问我为什么没有这个选择器写在上面的表格中，是这样的，这个选择器中有字符 `|`，这个字符在markdown表格中是表格的分界线。日了狗了.....

---

## CSS 现代选择器（2022+）

### :has() 伪类 - 父选择器

* 描述：选择包含特定后代的父元素，被称为"父选择器"
* 浏览器支持：Chrome 105+, Safari 15.4+, Firefox 121+

```css
/* 选择包含 img 子元素的 figure 元素 */
figure:has(img) {
    border: 2px solid blue;
}

/* 选择包含 .active 类子元素的父元素 */
.card:has(.active) {
    box-shadow: 0 0 10px rgba(0,0,0,0.3);
}

/* 选择直接包含 figcaption 的 figure */
figure:has(> figcaption) {
    background: #f5f5f5;
}

/* 表单验证：选择包含无效输入项的表单组 */
.form-group:has(input:invalid) {
    border-color: red;
}

/* 选择被聚焦的输入框所在的表单容器 */
form:has(input:focus) {
    background: #fffbf0;
}

/* 与 :not() 结合 */
.card:not(:has(img)) {
    padding-left: 0;
}
```

### :is() 和 :where() 伪类函数

* 描述：简化复杂的选择器列表

```css
/* :is() - 匹配任意一个选择器（保持特异性） */
:is(h1, h2, h3, h4, h5, h6) {
    font-family: sans-serif;
}

:is(header, article) :is(h1, h2, h3) {
    color: blue;
}

/* :where() - 匹配任意一个选择器（特异性为0） */
:where(h1, h2, h3) {
    font-size: 1.5em;
}

/* 容错性：即使其中一个选择器无效，整体仍然有效 */
:is(h1, h2, ::-webkit-scrollbar) {
    /* Firefox 不认识 ::-webkit-scrollbar，但 h1 和 h2 依然生效 */
    color: red;
}
```

### CSS 嵌套 (Nesting)

* 浏览器支持：Chrome 112+, Safari 16.5+, Firefox 117+

```css
/* 使用嵌套 */
.card {
    background: white;
    
    .title {
        font-size: 1.5rem;
        
        &:hover {
            color: blue;
        }
    }
    
    /* & 表示父选择器 */
    &:hover {
        box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
    
    /* 嵌套媒体查询 */
    @media (min-width: 768px) {
        padding: 20px;
    }
}

/* 选择器组合 */
.button {
    /* 生成 .button.primary */
    &.primary {
        background: blue;
    }
    
    /* 生成 .button, .link */
    &, .link {
        cursor: pointer;
    }
}
```

---

## CSS 容器查询 (Container Queries)

* 描述：基于容器大小而非视口大小应用样式
* 浏览器支持：Chrome 105+, Safari 16+, Firefox 110+

```css
/* 1. 定义容器 */
.card-container {
    container-type: inline-size;
    container-name: card;
}

/* 简写形式 */
.card-container {
    container: card / inline-size;
}

/* 2. 使用容器查询 */
@container (min-width: 400px) {
    .card {
        display: flex;
        flex-direction: row;
    }
}

@container card (min-width: 600px) {
    .card {
        font-size: 1.2rem;
    }
}
```

### 容器查询单位

```css
@container (min-width: 400px) {
    .item {
        width: 50cqw;        /* cqw - 容器查询宽度 */
        height: 30cqh;       /* cqh - 容器查询高度 */
        padding: 5cqi;       /* cqi - 容器查询行内尺寸 */
        margin-bottom: 2cqb; /* cqb - 容器查询块级尺寸 */
        font-size: 5cqmin;   /* cqmin / cqmax */
    }
}
```

---

## CSS 级联层 (Cascade Layers)

* 描述：通过 `@layer` 规则显式定义 CSS 的层叠顺序
* 浏览器支持：Chrome 99+, Safari 15.4+, Firefox 97+

```css
/* 定义层的顺序（越后定义优先级越高） */
@layer reset, base, components, utilities;

/* 在特定层中编写样式 */
@layer reset {
    *, *::before, *::after {
        box-sizing: border-box;
    }
    body {
        margin: 0;
    }
}

@layer base {
    body {
        font-family: system-ui, sans-serif;
        line-height: 1.5;
    }
}

@layer components {
    .btn {
        padding: 10px 20px;
        border: none;
        border-radius: 4px;
    }
}

/* 导入到特定层 */
@import url('reset.css') layer(reset);
@import url('bootstrap.css') layer(framework);

/* 覆盖框架样式 */
@layer custom {
    .btn {
        background: purple; /* 即使特异性相同，也会覆盖 bootstrap */
    }
}
```

---

## CSS 颜色函数

### oklch() 和 oklab()

```css
/* oklch：感知均匀的颜色空间 */
.element {
    color: oklch(70% 0.2 250);
    background: oklch(90% 0.05 120 / 0.5);
}

/* oklab */
.element {
    color: oklab(70% -0.1 0.2);
}
```

### color-mix()

```css
/* 混合两种颜色 */
.element {
    background: color-mix(in srgb, blue 70%, red);
    color: color-mix(in oklch, blue 50%, red);
}
```

### 相对颜色

```css
.element {
    --base: #3498db;
    
    /* 变亮 */
    color: hsl(from var(--base) h s calc(l + 20%));
    
    /* 变暗 */
    background: hsl(from var(--base) h s calc(l - 10%));
    
    /* 透明度变化 */
    border-color: rgb(from var(--base) r g b / 0.5);
}
```

---

## CSS 视口单位增强

```css
.element {
    /* 小视口单位（考虑地址栏收起状态） */
    height: 100svh;
    
    /* 大视口单位（考虑地址栏展开状态） */
    height: 100lvh;
    
    /* 动态视口单位（自动适应地址栏变化） */
    height: 100dvh;
}
```

---

## CSS 其他新特性

### text-wrap: balance / pretty

```css
.headline {
    text-wrap: balance;  /* 平衡短文本行的长度 */
    text-wrap: pretty;   /* 更好的断行 */
}
```

### @property 自定义属性

```css
/* 注册自定义属性 */
@property --gradient-angle {
    syntax: '<angle>';
    initial-value: 0deg;
    inherits: false;
}

.animated-gradient {
    background: linear-gradient(var(--gradient-angle), red, blue);
    animation: rotate 2s linear infinite;
}

@keyframes rotate {
    to {
        --gradient-angle: 360deg;
    }
}
```

### CSS 数学函数

```css
.element {
    width: clamp(300px, 50%, 800px);  /* 限制范围 */
    font-size: min(5vw, 20px);        /* 取最小值 */
    padding: max(2vw, 16px);          /* 取最大值 */
}
```