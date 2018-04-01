### Form提交参数处理

```javascript
// 封装jQuery插件
$.prototype.serializeObject = function() {
    var a, o, h, i, e;
    a = this.serializeArray();
    o = {};
    h = o.hasOwnProperty;
    for (i = 0; i < a.length; i++) {
        e = a[i];
        if (!h.call(o, e.name)) {
            o[e.name] = e.value;
        }
    }
    return o;
};

// use
$('form').submit(function(event) {
    event.preventDefault();

    var form = $(this);
    $.ajax({
        url: form.attr("action"),
        type: "POST",
        data: JSON.stringify(form.serializeObject()),
        contentType: "application/json",
        dataType: "json",
        beforeSend: function () {
        },
        error: function () {
        },
        complete:function () {
        },
        success: function (res) {
        }
    })
});
```