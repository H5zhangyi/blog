## Sublime Text3安装破解
> 官网下载地址: [https://www.sublimetext.com/3](https://www.sublimetext.com/3)
### 软件破解
选项 help -> license (输入注册码，可以一行一行粘贴)

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

> [备用注册码](http://blog.sina.com.cn/s/blog_68e267e10102v76h.html)
### 安装package control（https://packagecontrol.io/ ）

提醒：装完了所有插件都要重启软件才可以生效

1. 通过快捷键 ctrl+` 或者 View > Show Console 菜单打开控制台。
2. 粘贴如下代码（https://packagecontrol.io/installation）：

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

### 常用工具类
- sublimecodeintel 代码自动补全(在某类型代码环境下，html,css,js等)
- emmet 快速的html/css编写神器
- sidebarenhancements 增强侧边栏的插件，浏览器预览插件
- BracketHighlighter 代码高亮
### sublime F12预览：preference -> key Bindings 更改路径为谷歌安装地址（如下）
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

### 插件卸载

1. 通过ctrl+shift+p打开命令面板，通过输入remove找到:remove package回车，出现已安装列表，选中回车删除。
2. Preferences-browse packages...(不推荐，容易导致误删除)

### Sublime支持less

1. 安装sublime插件

- 安装less2css插件：
    作用：a.当保存less文件的时候自动生成同名的css文件；
        b.当保存less文件的时候提示编译错误信息；
        c.批量编译项目目录下的所有less文件为css文件。
    方法：ctrl+shift+p>install Package>输入less2css按Enter 
- 安装less插件
    作用：让less代码高亮
    方法：ctrl+shift+p>install Package>输入less按Enter 

2. 安装node.js 官网下载安装

3. 安装less
    cmd命令下：npm install -g less

之后,在sublime 里面建 less文件时会跳出一个错误

    LESS: Unable to interpret argument clean-css

  这就需要最后一步了

4. less-plugin-clean-css插件的安装
    npm install less-plugin-clean-css

> ps：插件安装完成重启sublime才会生效


### 将.md文件转换成.html文件

    npm install -g i5ting_toc //在npm命令窗口全局下载i5ting_toc
    i5ting_toc -f 文件名.md // 在md文档路径下开启npm命令窗口，输入命令，就可以转换了