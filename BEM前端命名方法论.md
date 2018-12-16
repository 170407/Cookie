#### BEM前端命名方法论

---

###### 前言

​	BEM--块(block)、元素(element)、修饰符(modifier).

---

###### 命名模式

 ```css
.block {}
.block__element {}
.block--modifier {}
 ```

        -  ```.block```代表更高级别的抽象或组件
        - ```.block__element```代表```.block```的后代，用于形成一个完整的```.block```的整体
        - ```.block--modifier```代表```.block```的不同状态或不同版本

之所以使用两个连字符和下划线而不是一个，是为了让自定义的块可以用单个连字符来界定，如:

```css
.site-search {} /*块*/
.site-search__field {} /*元素*/
.site-search--full {} /*修饰符*/
```

BEM的关键是凭借名字可以告诉其他开发者某个标记是用来干什么的.通过浏览HTML代码中class属性，就能明白模块之间是如何关联的: 有一些仅仅是组件，有一些则是这些组件的子孙或者是元素，还有一些是组件的其他形态或者修饰符。

例:

```css
.person {}
.person__hand {}
.person--female {}
.person--female__hand {}
.person__hand--left {}
```

反例:

```css
.person {}
.hand {}
.female {}
.female-hand {}
.left-hand {}
```

这些‘常规’CSS都是有意义的，但是它们之间却有些脱节。

使用BEM可以获得更多的描述和更加清晰的结构，单单通过代码中的命名就可以知道元素之间的关联。

常规方式命名:

```html
<form class = "site-search full">
  <input type = "text" class = "field">
  <input type = "Submit" value = "Search" class = "button">
</form>
```

这些CSS类名不太精确，并不能告知足够的信息。尽管可以用它们完成工作，但它们非常含糊不清。

BEM记号法:

```html
<form class = "site-search site-search--full">
  <input type = "text" class = "site-search__field">
  <input type = "Submit" value = "Search" class = "site-search__button">
</form>  
```

有个叫.site-search的块，它内部是一个叫.site-search__field的元素。并且.site-search还有另外一种形态叫.site-search--full

如果熟悉OOCSS(面向对象CSS), 对media对象一定也不陌生。用BEM方式, media对象如下所示:

```css
.media {}
.media__img {}
.media__img--rev {}
.media__body {}
```

```html
<div class = "media">
  <img src = "logo.png" alt = "logo" class = "media__img--rev">
  <div class = "media__body">
    <h3 class = "alpha">alpha</h3>
    <p class = "lede">lede</p>
  </div>
</div> 
```

---

###### 用不用BEM？

例:

```css
.header {}
.header__logo {}
```

​	使用BEM的诀窍是，要知道什么时候哪些东西是应该写成BEM格式的。因为某些东西确实是位于一个块的内部，但这并不意味它就是BEM中所说的元素。这个例子中，网站logo完全是恰巧在.header的内部，它也有可能在侧边栏或是页脚里面。一个元素的范围可能开始于任何上下文，因此要确定只在所需要用到BEM的地方才使用它。

例:

```css
.site-logo {}
.site-logo--xmas {}
```

​	然而，一切都有可能潜在地用到BEM。再来看一下.site-logo的例子，想象一下想要给网站增加一点圣诞节的气氛，想有一个圣诞版的logo。可以通过使用--修饰符来快速地为代码构建另一个版本.

