1.官网下载：http://www.sublimetext.com/3

2.破解 选项 help -> license  （输入注册码，可以一行一行粘贴）

 —– BEGIN LICENSE —–
Michael Barnes
Single User License
EA7E-821385
8A353C41 872A0D5C DF9B2950 AFF6F667
C458EA6D 8EA3C286 98D1D650 131A97AB
AA919AEC EF20E143 B361B1E7 4C8B7F04
B085E65E 2F5F5360 8489D422 FB8FC1AA
93F6323C FD7F7544 3F39C318 D95E6480
FCCC7561 8A4A1741 68FA4223 ADCEDE07
200C25BE DBBC4855 C4CFB774 C5EC138C
0FEC1CEF D9DCECEC D3A5DAD1 01316C36
—— END LICENSE ——

备用注册码：http://blog.sina.com.cn/s/blog_68e267e10102v76h.html

3.安装package control（https://packagecontrol.io/ ）

提醒：装完了所有插件都要重启软件才可以生效

1)通过快捷键 ctrl+` 或者 View > Show Console 菜单打开控制台。

2)粘贴如下代码（https://packagecontrol.io/installation）：
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88';
pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); 
urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) );
by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); 
dh = hashlib.sha256(by).hexdigest(); 
print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) 
if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

 安装结束后：
  1 missing dependency was just installed.
  Sublime Text should be restarted, otherwise one or more of the installed packages may not function properly.”
  说的是一个依赖包安装好后，软件需要重启。
  通过ctrl+shift+p打开命令面板，
  然后输入 pci找到:package control:install Package,回车，出现插件列表说明安装成功了。
  
 然后在列表中选中要安装的插件。
 
  常用工具类：
  sublimecodeintel 代码自动补全(在某类型代码环境下，html,css,js等)
  emmet 快速的html/css编写神器
HTML文档需要包含一些固定的标签，比如<html>、<head>、<body>等，
  现在1秒钟就可以输入这些标签：比如输入“!”或“html:5”，然后按ctrl+E键;输入标签元素，按Ctrl+E或者tab，即可产生这一对标签。
  如：输入style,在emmet语法最后按下Ctrl+E或者tab，即可得到  连续输入元素名称和ID，Emmet会自动为你补全，比如输入p#foo
 
     Emmet更多用法：
     http://www.open-open.com/lib/view/open1451954899292.html
     http://defcon.cn/2416.html
     https://www.douban.com/note/299285545/
     Emmet快捷方式查询

     html5 html5新增标签、属性的提示（安装了sublimecodeintel ，会有提示，例如input.）
     
     colorPicker:调出系统调色板（先装.net framework）
     
      key-bindings: {"keys": ["ctrl+shift+c"], "command": "color_pick"},
     javascript completions: js语法提示
     
     Autofilename:自动补全路径 （img src...）
     
    浏览器预览：
    菜单方式：sidebarenhancements（增强侧边栏的插件，浏览器预览插件）
    sidebarenhancements.txt
    快捷键方式:openinbrowser（必须先安装sidebarenhancements）
    openinbrowser.txt
    
  美化：
    theme 主题（package control 官网:https://packagecontrol.io/ ）
    aligments   对齐：key-bindings:{"keys": ["ctrl+alt+f"],"command":"alignment"}
    BracketHighlighter 代码高亮
    Color Highlighter它可以展示你所选择的颜色代码的真正颜色。同时包含一个颜色选择器让你可以方便地更改颜色。
  
  sublime F12预览：preference -> key Bindings 更改路径为谷歌安装地址（如下）
[
 { "keys": ["f12"], "command": "side_bar_files_open_with",
"args": {
"paths": [],
"application": "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe",
"extensions":".*" //any file with extension
} },
{ "keys": ["ctrl+f12"], "command": "side_bar_files_open_with",
"args": {
"paths": [],
"application": "D:\\firefox.exe",
"extensions":".html" //any file with extension
} },
]
    
packagecontrol插件官网：https://packagecontrol.io/ 

插件卸载：
1.通过ctrl+shift+p打开命令面板，通过输入remove找到:remove package   	回车，出现已安装列表，选中回车删除。
2.Preferences-browse packages...(不推荐，容易导致误删除)
