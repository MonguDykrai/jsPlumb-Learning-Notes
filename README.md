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

## save and load

Save

```js
$.each(jsPlumb.getConnections(), function (idx, connection) {
    connections.push({
    connectionId: connection.id,
    pageSourceId: connection.sourceId,
    pageTargetId: connection.targetId,
    anchors: $.map(connection.endpoints, function(endpoint) {

      return [[endpoint.anchor.x, 
      endpoint.anchor.y, 
      endpoint.anchor.orientation[0], 
      endpoint.anchor.orientation[1],
      endpoint.anchor.offsets[0],
      endpoint.anchor.offsets[1]]];

    })
  });
});
```

Load

```js
$.each(connections, function( index, elem ) {
    var connection1 = jsPlumb.connect({
    source: elem.pageSourceId,
    target: elem.pageTargetId,
    anchors: elem.anchors
  });

});
```

<https://stackoverflow.com/questions/20620719/save-and-load-jsplumb-flowchart-including-exact-anchors-and-connections>

## Connectors

### gap

> optional, defaults to 0 pixels. Lets you specify a gap between the end of the Connector and the elements to which it is attached.

![](./images/Snipaste_2019-03-17_06-15-24.png)

### cornerRadius

![](./images/Snipaste_2019-03-17_06-17-56.png)

<http://jsplumb.github.io/jsplumb/connectors.html>

## getUuid | getUuids

```js
jsPlumb.bind("connection", function (conn, originalEvent) {
  console.log(conn.targetEndpoint.getUuid());
});
```

```js
const endpoint = jsPlumb.addEndpoint(
  $("#" + id),
  {
    uuid: id + "lt-in",
    isTarget: true,
    anchor: [0, 0.2]
  }
);

console.log(endpoint.getUuid());
```

```js
$.each(jsPlumb.getConnections(), function (idx, connection) {
  // console.log(connection.getUuids()); // ["decisioncontainer1rm-out", "decisioncontainer2lm-in"]

  connections.push({
    // connectionId: connection.id,
    sourceId: connection.sourceId,
    targetId: connection.targetId,
    uuids: connection.getUuids(), // getUuids
    anchors: $.map(connection.endpoints, function(endpoint) {
      console.error(endpoint.getUuid());
      // console.log(endpoint)

      return [
        [
          endpoint.anchor.x, 
          endpoint.anchor.y, 
          // endpoint.anchor.orientation[0], 
          // endpoint.anchor.orientation[1],
          // endpoint.anchor.offsets[0],
          // endpoint.anchor.offsets[1]
        ]
      ];

    })
  });
});
```

### 使用 uuid 回显

![](./images/回显.gif)

```js
$.each(connections, function (index, elem) {
  console.log(elem)
  // jsPlumb.connect({
  //   source: elem.sourceId,
  //   target: elem.targetId,
  //   anchors: elem.anchors
  // });

  jsPlumb.connect({
    uuids: elem.uuids
  });
});
```

<https://community.jsplumbtoolkit.com/apidocs/classes/Endpoint.html#method_getUuid>