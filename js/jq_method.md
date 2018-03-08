### jq方法

.add(selector)添加元素到匹配的元素集合
支持多数$("")选择器

```
$("p").add("div").addClass("widget")

$('li').add(document.getElementsByTagName('p')[0])

$('li').add('<p id="new">new paragraph</p>').css('background-color', 'red');

<script>$("p").clone().add("<span>Again</span>").appendTo(document.body);</script>
```
