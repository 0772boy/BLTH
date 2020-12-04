<p align ="center"><img src="https://cdn.jsdelivr.net/gh/andywang425/BLTH@7d7ca494edd314806460e24c6b59be8ae1bd7dc6/img/script-icon.png"></p>
<p align="center"><img src="https://img.shields.io/badge/TamperMonkey_4.10-pass-green.svg" alt="TamperMonkey 4.10"> <img src="https://img.shields.io/badge/Chromium_83-pass-green.svg" alt="Chromium 83"> <img src="https://img.shields.io/badge/Firefox_77-pass-green.svg" alt="Firefox 77">&nbsp;<img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License">&nbsp;<img src="https://img.shields.io/github/stars/andywang425/Bilibili-SGTH?style=social" alt=""></p>
<h1 align="center">Bilibili Live Tasks Helper</h1>

-------------------------------

### 安装方法
### 1. 点击 [BLTH_raw](https://raw.githubusercontent.com/andywang425/BLTH/master/B%E7%AB%99%E7%9B%B4%E6%92%AD%E9%97%B4%E6%8C%82%E6%9C%BA%E5%8A%A9%E6%89%8B.user.js) 从 github 安装脚本    
### 2. 点击 [BLTH_Origin_greasyfork](https://greasyfork.org/zh-CN/scripts/406048-b%E7%AB%99%E7%9B%B4%E6%92%AD%E9%97%B4%E6%8C%82%E6%9C%BA%E5%8A%A9%E6%89%8B) 前往 greasyfork 安装脚本  
### 3. 点击 [BLTH_Origin_openuserjs](https://openuserjs.org/scripts/andywang425/B%E7%AB%99%E7%9B%B4%E6%92%AD%E9%97%B4%E6%8C%82%E6%9C%BA%E5%8A%A9%E6%89%8B) 前往 openuserjs 安装脚本  

-------------------------------

### 使用方法 
在[Tampermonkey](https://www.tampermonkey.net/)中启用脚本，登陆bilibili后打开任意b站直播间。 
+ 在 [Tampermonkey](https://www.tampermonkey.net/) 脚本设置中需要将此脚本的设置 “仅在顶层页面（框架）运行” 设置为否(默认为否)才使脚本在特殊直播间运行。  
+ 不保证能通过其它油猴插件(Greasemonkey/Violentmonkey等)运行。  
-------------------------------

### 一些建议
+ 初次使用时若出现看不到控制面板的情况，请等待一会或尝试刷新(`shift+F5`)页面。  
+ 部分设置更改后需要刷新页面才能生效。  
+ 使用前建议先关闭广告拦截插件，并确认相关浏览器设置(如cookie权限，脚本拦截)否则该脚本可能无法正常运行。  
+ 建议通过修改浏览器设置缩减或不发送Referer。
  <details>
  <summary>点击展开具体方法</summary>

  + Chrome  
  在地址栏输入`chrome://flags`，搜索`Reduce default 'referer' header granularity`将这个功能设置为`Enabled`。
  + Edge  
  在地址栏输入`edge://flags`，搜索`Reduce default 'referer' header granularity`将这个功能设置为`Enabled`。
  + FireFox   
  在地址栏输入`about:config`，搜索`network.http.sendRefererHeader`，把这个设置的值改为`0`。
  + 建议这样做的原因：
  B站直播间api在被调用时，其referer值为`https://live.bilibili.com/当前房间号`。所以若不修改设置，脚本发出的相当一部分api请求所携带的referer值是不合理的。如在直播间`777`使用脚本，参加了直播间`666`的天选时刻，那么发出请求所携带的referer值就是`https://live.bilibili.com/777`。但正常情况下天选时刻只能在对应房间参加，如果B站有相关检测的话很容易发现刚刚那个请求是异常的。  
  + 请注意：
  某些网站为了防盗链要求referer必须为本站链接，不发送referer可能导致无法正常访问这些网站。同时不发送referer还可能会影响网站的广告收入。
  
  </details>

交流qq群:[1106094437](https://jq.qq.com/?_wv=1027&k=fCSfWf1O)（入群问题答案：B站直播间挂机助手），欢迎进来聊天或者提点建议~    

-------------------------------

## 功能细节 

脚本窗口可以上下滚动！部分设置可能需要滚动后才能看到。
点击**直播画面上方**按钮隐藏/显示脚本窗口和提示信息。    

<details>
<summary>自动参加礼物抽奖</summary>
<ul>
<li>抽奖前随机延迟</li>
<li>随机跳过抽奖</li>
<li>抽奖前模拟进入目标房间</li>
<li>抽奖前发送活跃弹幕（防检测）</li>
</ul>
</details>
<details>
<summary>自动参加实物（金宝箱）抽奖</summary>
<ul>
<li>忽略含特定关键字或匹配特定正则表达式的存疑抽奖</li>
</ul>
</details>
<details>
<summary>自动参与天选时刻</summary>
<ul>
<li>忽略所需金瓜子大于设置值的天选</li>  
<li>忽略含特定关键字或匹配特定正则表达式的存疑天选</li>
<li>尝试识别天选中的金额并忽略金额低于设置值的天选</li>
<li>保存当前关注列表为白名单/取关不在白名单内的UP主</li>  
<li>上传天选信息至自己的直播间/从特定直播间获取天选信息</li>
<li>把参与天选时关注的UP移动到新关注分组/取关该分组内的UP主</li>
<li>未中奖自动取关</li>
<li>中奖后自动发私信/弹幕</li>
</ul>
</details>
<details>
<summary>自动完成主站每日任务</summary>
<ul>
<li>登陆主站</li>  
<li>观看视频</li>  
<li>自动投币（可指定给某用户的视频投币）</li>  
<li>分享视频</li>   
</ul>
</details>
<details>
<summary>屏蔽不必要的内容</summary>
<ul>
<li>移除2233模型</li>
<li>移除活动入口</li>
<li>移除排行榜</li>
<li>屏蔽挂机检测</li>
</ul>
</details>
<li>自动获取小心心</li>
<li>发送粉丝勋章打卡弹幕</li>
<li>自动送礼</li>
<li>银瓜子换硬币</li>
<li>直播区签到</li>
<li>应援团签到</li>
<li>自动参加被广播的节奏风暴</li>
<li>自动发弹幕</li>
<li>快捷购买粉丝勋章</li>
<li>隐身入场</li><br>

-------------------------------

## 说明
#### 脚本代码格式
本脚本在三个平台上的代码格式有所不同
+ github: 压缩和原格式都有
+ openuserjs: 原格式
+ greasyfork: 原格式

注：项目文件中的[B站直播间挂机助手.user.js](https://github.com/andywang425/BLTH/blob/master/B%E7%AB%99%E7%9B%B4%E6%92%AD%E9%97%B4%E6%8C%82%E6%9C%BA%E5%8A%A9%E6%89%8B.user.js)是压缩后的脚本。  
原格式的脚本为[B站直播间挂机助手.js](https://github.com/andywang425/BLTH/blob/master/B%E7%AB%99%E7%9B%B4%E6%92%AD%E9%97%B4%E6%8C%82%E6%9C%BA%E5%8A%A9%E6%89%8B.js)。  

#### 脚本内置说明
运行脚本后点击控制面板上带下划线的小问号查看各项功能的具体说明。  

#### 运行日志
+ 普通的日志可以点击聊天区上方，大航海右侧的【日志】查看。
+ 脚本默认关闭控制台日志。勾选控制面板上的`其他设置 - 控制台日志`即可开启。  
  打开控制台在Filter中输入`IGIFTMSG`即可过滤出本脚本的日志。

#### 关于反馈
+ 如果使用脚本过程中遇到问题，可以先按上述步骤开启控制台日志，然后再次运行脚本并在控制台中寻找相关错误信息。  
  若能找到请在反馈bug时附上这些控制台日志。
+ 反馈bug前请先阅读[bug_report.md](https://github.com/andywang425/BLTH/blob/master/.github/ISSUE_TEMPLATE/bug_report.md)。

-------------------------------

## 已知问题
1. [#12](https://github.com/andywang425/BLTH/issues/12)  
本脚本可能与[Bilibili-Evolved](https://github.com/the1812/Bilibili-Evolved)存在兼容性问题导致脚本窗口无法正确加载。若出现此问题，请尝试在Bilibili-Evolved设置-其它中，将`加载模式`设置为延后，打开`启用Ajax Hook API`。  
2. 脚本每次更新后第一次运行可能会不工作，`shift+F5`刷新一下页面即可。   

-------------------------------

## 许可证
<a href = "https://github.com/andywang425/BLTH/blob/master/LICENSE" style="font-size: 1.1em;">MIT License</a>

-------------------------------

## 其它信息  
这个项目的部分代码来源于以下几个项目:  
+ [B站直播签到助手](https://greasyfork.org/zh-CN/scripts/381907-b%E7%AB%99%E7%9B%B4%E6%92%AD%E7%AD%BE%E5%88%B0%E5%8A%A9%E6%89%8B) (MIT) by [十六夜](https://greasyfork.org/en/users/289469-%E5%8D%81%E5%85%AD%E5%A4%9C)
+ [BLRHH](https://github.com/SeaLoong/BLRHH) (MIT) by [SeaLoong](https://github.com/SeaLoong)  
+ [Bilibili-LRHH](https://github.com/pjy612/Bilibili-LRHH) (MIT, _forked from SeaLoong/BLRHH_) by [pjy612](https://github.com/pjy612)
+ [TampermonkeyJS](https://github.com/lzghzr/TampermonkeyJS) (MIT) by [lzghzr](https://github.com/lzghzr)  
+ [layer](https://github.com/sentsin/layer) (MIT) by [sentsin](https://github.com/sentsin)  
+ [Ajax-hook](https://github.com/wendux/Ajax-hook) (MIT) by [wendux](https://github.com/wendux)

本脚本使用的库：  
+ [jquery](https://github.com/jquery/jquery) (MIT)  
+ [BilibiliAPI_Mod.min.js](https://github.com/andywang425/BLTH/blob/master/library_files/BilibiliAPI_Mod.js) (MIT)：B站API及常用函数。  
+ [libBilibiliToken.js](https://github.com/lzghzr/TampermonkeyJS/blob/master/libBilibiliToken/libBilibiliToken.js) (MIT)：获取移动端token。  
+ [libWasmHash.js](https://github.com/lzghzr/TampermonkeyJS/blob/master/libWasmHash/libWasmHash.js) (MIT)：WebAssembly实现的Hash，计算心跳请求参数。  
+ [layer.js](https://github.com/sentsin/layer/blob/master/dist/layer.js) (MIT)：web弹层组件。  
+ [Ajax-hook.min.js](https://github.com/wendux/Ajax-hook) (MIT)：用于拦截浏览器XMLHttpRequest的库。  

本脚本引用的外部资源：  
+ [layer.css](https://github.com/sentsin/layer/blob/master/dist/theme/default/layer.css)：layer.js的内置样式  

-------------------------------

## 鸣谢
[十六夜](https://greasyfork.org/en/users/289469-%E5%8D%81%E5%85%AD%E5%A4%9C)，[SeaLoong](https://github.com/SeaLoong)，[pjy612](https://github.com/pjy612)，[lzghzr](https://github.com/lzghzr)，[sentsin](https://github.com/sentsin)，[wendux](https://github.com/wendux)，[风绫丨钰袖](https://space.bilibili.com/20842051)，[Server酱](https://sc.ftqq.com/)，[无尾玦的小尾巴](https://space.bilibili.com/234368216)  
以及所有提出过建议的用户。

-------------------------------

## 更新日志
>### 5.6.3
>新增两种能识别的天选时刻种类；直播画面全屏后自动关闭面板；修复移动分组等网络请求被风控使脚本停止运行的问题；新增控制台日志选项；若启用需创分组的功能则不创建；新选项：不参与加密直播间的天选；优化了请求失败后再次尝试发起请求的逻辑。

完整更新日志见[update-log.md](https://github.com/andywang425/BLTH/blob/master/update-log.md)。  