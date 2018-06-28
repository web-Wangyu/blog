---
title: 第四天-vue+Hbuilder制作安卓app
thumbnail: "http://lc-thex246k.cn-n1.lcfile.com/022df6d7d8bb7d47c11b.png"
---

# 第四天-vue+Hbuilder制作安卓app

### 前言

通过前段时间自学vue，基本熟悉了vue框架，这是一款方便易学的MVVM框架。
为了能让所学知识融汇贯通在一起，决定制作一款记录密码的app。

### 使用技术

UI使用[mdui框架](https://www.mdui.org/docs/dialog)，这是一款我个人很喜欢的UI框架，扁平化的设计风格，简洁实用的动效。

app没有使用vue路由进行跳转，使用的是Hbulider的mui中webview，进行跳转页面。这样好处在于mui会自动监听手机的返回按键，使用vue-router跳转使用Hbuilder打包app，按下返回按键后会直接退出app。

后台使用leancloud云后台，简单好用，方便我这种不会后台语言的人。
### 效果展示

app打开后通过mui方法获取设备id，通过设备id在后台查看是否注册，如果没有打开注册页面。

![login](http://lc-thex246k.cn-n1.lcfile.com/f947073d2bf5defe9457.gif)

app打开后通过mui方法获取设备id，通过设备id在后台查看是否注册，如果有打开登录页面。如果遗忘密码可以通过昵称找回。

![index](http://lc-thex246k.cn-n1.lcfile.com/1662dc8e33c7456fc6cf.gif)

添加新的密码。用户这个子页面可以修改用户头像，由于是使用的app模拟器，调不出图库，没有演示。

![add](http://lc-thex246k.cn-n1.lcfile.com/e33561d42c45e25f63c9.gif)

### 部分代码展示

给底部导航栏设置webview路径，并设置上下要留出的空间。

```
		mui.init();
		var subpages = ['html/content.html', 'html/user.html'];
		var subpage_style = {
			top: '45px',
			bottom: '51px'
		};

    //当前激活选项
		var activeTab = subpages[0];
		//选项卡点击事件
		mui('.mui-bar-tab').on('tap', 'a', function(e) {
			var targetTab = this.getAttribute('href');
			if(targetTab == activeTab) {
				return;
			}
			//显示目标选项卡
			plus.webview.show(targetTab);
			//隐藏当前;
			plus.webview.hide(activeTab);
			//更改当前活跃的选项卡
			activeTab = targetTab;
			if(activeTab == 'html/user.html') {
				document.getElementById('title').innerHTML = '用户'
			} else {
				document.getElementById('title').innerHTML = '首页'
			}

		});

```
通过关闭手机返回按键的监听，使登录页面不能通过按键返回，只能登录才能查看；

```
		mui.init({
			keyEventBind: {
				backbutton: true //关闭back按键监听
			}
		})

```

通过点击图标，切换密码显示与隐藏,与图标的样式。

```
chack: function() {
	this.type == 'password' ? this.type = 'text' : this.type = 'password';
	this.see == 'visibility' ? this.see = 'visibility_off' : this.see = 'visibility';
					},

```

点击跳转详细页面，通过mui方法跳转并将当前的数据id传递给详细页面。

```
					info: function(v) {
						mui.openWindow({
							url: 'info.html',
							id: 'info.html',
							extras: {
								objectid: v.id
							}
						})
					}
```

### 总结

使用vue需要时刻注意，要改变自己的思考方式。就像最简单的点击修改div的样式，下意识我还是会想去通过点击事件获取DOM节点，并通过操纵DOM去修改样式。但是使用vue后，我只需要通过点击事件修改相应的数据，利用:class实现Class 与 Style 绑定，省去繁琐操作。

[GitHub地址](https://github.com/web-Wangyu/vue-pas)

###### Never quit, keep up with it。
