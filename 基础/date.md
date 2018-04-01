# JS操作时间(date相关)

### 获取当前时间

> var myDate = new Date(); 

    myDate.toLocaleDateString()；// 可以获取当前日期
    myDate.toLocaleTimeString(); // 可以获取当前时间

### 扩展

```javascript
    myDate.getYear(); //获取当前年份(2位)
    myDate.getFullYear(); //获取完整的年份(4位,1970-????)
    myDate.getMonth(); //获取当前月份(0-11,0代表1月)
    myDate.getDate(); //获取当前日(1-31)
    myDate.getDay(); //获取当前星期X(0-6,0代表星期天)
    myDate.getTime(); //获取当前时间(从1970.1.1开始的毫秒数)
    myDate.getHours(); //获取当前小时数(0-23)
    myDate.getMinutes(); //获取当前分钟数(0-59)
    myDate.getSeconds(); //获取当前秒数(0-59)
    myDate.getMilliseconds(); //获取当前毫秒数(0-999)
    myDate.toLocaleString( ); //获取日期与时间

### 日期格式化
```

```javascript
    //---------------------------------------------------  
    // 日期格式化  
    // 格式 YYYY/yyyy/YY/yy 表示年份  
    // MM/M 月份  
    // W/w 星期  
    // dd/DD/d/D 日期  
    // hh/HH/h/H 时间  
    // mm/m 分钟  
    // ss/SS/s/S 秒  
    //---------------------------------------------------  
    Date.prototype.Format = function(formatStr)   
    {   
        var str = formatStr;   
        var Week = ['日','一','二','三','四','五','六'];  
      
        str=str.replace(/yyyy|YYYY/,this.getFullYear());   
        str=str.replace(/yy|YY/,(this.getYear() % 100)>9?(this.getYear() % 100).toString():'0' + (this.getYear() % 100));   
      
        str=str.replace(/MM/,this.getMonth()>9?this.getMonth().toString():'0' + this.getMonth());   
        str=str.replace(/M/g,this.getMonth());   
      
        str=str.replace(/w|W/g,Week[this.getDay()]);   
      
        str=str.replace(/dd|DD/,this.getDate()>9?this.getDate().toString():'0' + this.getDate());   
        str=str.replace(/d|D/g,this.getDate());   
      
        str=str.replace(/hh|HH/,this.getHours()>9?this.getHours().toString():'0' + this.getHours());   
        str=str.replace(/h|H/g,this.getHours());   
        str=str.replace(/mm/,this.getMinutes()>9?this.getMinutes().toString():'0' + this.getMinutes());   
        str=str.replace(/m/g,this.getMinutes());   
      
        str=str.replace(/ss|SS/,this.getSeconds()>9?this.getSeconds().toString():'0' + this.getSeconds());   
        str=str.replace(/s|S/g,this.getSeconds());   
      
        return str;   
    } 
```

### ES6封装

```
/**
 * 传入秒数，时间格式化
 */
export function formatDate(date1, fmt) {
  const date = new Date(date1 * 1000)
  if (/(y+)/.test(fmt)) {
    fmt = fmt.replace(RegExp.$1, (date.getFullYear() + '').substr(4 - RegExp.$1.length))
  }
  const o = {
    'M+': date.getMonth() + 1,
    'd+': date.getDate(),
    'h+': date.getHours(),
    'm+': date.getMinutes(),
    's+': date.getSeconds()
  }
  for (const k in o) {
    if (new RegExp(`(${k})`).test(fmt)) {
      const str = o[k] + ''
      fmt = fmt.replace(RegExp.$1, (RegExp.$1.length === 1) ? str : padLeftZero(str))
    }
  }
  return fmt
}

function padLeftZero(str) {
  return ('00' + str).substr(str.length)
}
```
