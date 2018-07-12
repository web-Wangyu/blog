---
title: 第六天-使用URL Scheme通过web唤醒App
thumbnail: "http://lc-thex246k.cn-n1.lcfile.com/9dceed69cebe45c2f618.png"
---

# 使用URL Scheme通过web唤醒App

### 上干货
现在我们经常会遇到，明明点击的是一个连接，却跳到App内 了，在很多电商页面上，也会有提示，应用内打开，那么这种是基于什么实现的呢？在web前端，称之为deep link ,你点击链接的时候，它回去判断你本地是不是安装了程序，如果安装了，则调动app，这是通过自定义url scheme来实现的。

例如：<a class="btn" onclick='window.location.href = "openapp.jdmobile://"'>京东</a>

一定要手机内装有相关App，否则会出错。

### 核心代码

``` 
window.location.href = "openapp.jdmobile://"   
```
### 常用URL Scheme

| 应用名称 | URL Scheme |
| --------   | -----:   | :----: |
| 微博 | weibo:// |
| QQ | mqq:// |
| QQ群组 | mqqapi://card/show_pslcard?src_type=internal&version=1&card_type=group&uin={QQ群号} |
| QQ联系人 | mqqapi://card/show_pslcard?src_type=internal&version=1&uin={QQ号码} |
| 支付宝 | alipay:// |
| 微信 | weixin:// |
| 微信 | wechat:// |
| 微信-扫一扫 | weixin://dl/scan |
| 微信-反馈 | weixin://dl/feedback |
| 微信-朋友圈 | weixin://dl/moments |
| 微信-设置 | weixin://dl/settings |
| 微信-消息通知设置 | weixin://dl/notifications |
| 微信-聊天设置 | weixin://dl/chat |
| 微信-通用设置 | weixin://dl/general |
| 微信-公众号 | weixin://dl/officialaccounts |
| 微信-游戏 | weixin://dl/games |
| 微信-帮助 | weixin://dl/help |
| 微信-反馈 | weixin://dl/feedback |
| 微信-个人信息 | weixin://dl/profile |
| 微信-功能插件 | weixin://dl/features |
| 虾米音乐 | xiami:// |
| chrome | googlechrome:// |
| 微博国际版 | weibointernational:// |
| 摩拜单车 | mobike:// |
| ofo | ofoapp:// |
| 有道云笔记 | youdaonote:// |
| 印象笔记 | evernote:// |
| 今日头条 | snssdk141:// |
| 网易新闻 | newsapp:// |
| 网易云音乐 | orpheuswidget:// |
| QQ音乐 | qqmusic:// |
| QQ音乐最近播放 | qqmusic://today?mid=31&k1=2&k4=0 |
| 美团外卖 | meituanwaimai:// |
| 美团 | imeituan:// |
| Gmail | googlegmail:// |
| 网易邮箱 | neteasemail:// |
| QQ邮箱 | qqmail:// |
| 腾讯视频 | tenvideo:// |
| 爱奇艺 | iqiyi:// |
| 12306 | cn.12306:// |
| 有道词典 | yddict:// |
| 钉钉 | dingtalk:// |
###### Never quit, keep up with it。
