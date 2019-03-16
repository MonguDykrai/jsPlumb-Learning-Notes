# jsPlumb

## jQuery

### .appendTo

> Insert every element in the set of matched elements to the end of the target.

```html
<div id="app">
  <h1>jQuery</h1>
</div>

<script>
  $('<p>I love you.</p>').appendTo($('#app'))
</script>
```

![](./images/Snipaste_2019-03-16_20-23-04.png)

#### 可以省略闭合标签

```html
<div id="app">
  <h1>jQuery</h1>
</div>

<script>
  $('<p>I love you.</p>').appendTo($('#app'))

  $('<span style="display: inline-block; width: 30px; height: 10px; background: purple;">').appendTo($('#app')) // span 未写 “闭合” 标签
</script>
```

![](./images/Snipaste_2019-03-16_20-44-17.png)

Codepen: <https://codepen.io/MonguDykrai/pen/RdyGjL>

<http://api.jquery.com/appendto/>

### .html()

#### .html(htmlString)

> A string of HTML to set as the content of each matched element.

```html
<div id="app">
  <h1>jQuery</h1>
</div>

<script>
  $('<p>').appendTo($('#app')).html('<span>I love you.')
</script>
```

![](./images/Snipaste_2019-03-16_20-57-16.png)

Codepen: <https://codepen.io/MonguDykrai/pen/MxGbwK>

<http://api.jquery.com/html/>