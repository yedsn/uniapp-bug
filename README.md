## 详细问题描述

uniapp微信小程序端使用了v-slot之后无法获取获取当前页面定义的data和methods

## 附件

测试bug项目地址：https://github.com/yedsn/uniapp-bug

## 重现步骤

[步骤]
1. 比如有一个组件，在slot中携带一个值，组件内容如下
```html
<template>
	<view>
		<slot componentValue="我是组件里的值"/>
	</view>
</template>
```
2. 页面调用这个组件，使用v-slot获取组件携带的值，然后在v-slot里面又想获取当前页面的某个值或方法，页面内容如下
```html
<template>
	<view>
		{{pageValue}}
		<slot-component>
			<template v-slot="{componentValue}">
				{{pageValue}}
				<view>{{componentValue}}</view>
			</template>
		</slot-component>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				pageValue: '我是页面的值'
			}
		}
	}
</script>
```
[结果]
在H5端，页面的显示效果是这样的：

![](http://p2.so.qhmsg.com/t02aaad9adfa6676b0e.jpg)

而在小程序端，页面显示效果却是这样：

![](http://p2.so.qhmsg.com/t028865418407a85f0f.jpg)

就是使用了v-slot之后，v-slot里面就获取不到页面定义的值和方法等

[期望]

希望小程序使用了v-slot，还能跟没有使用v-slot的地方一样，可以获取页面定义的值，调用页面定义的方法

## IDE运行环境说明

[HBuilder 或 HBuilderX。如果你用其他工具开发uni-app，也需要在此说明]

HBuilderX

[IDE版本号]

2.6.16.20200424

[windows版本号]

Windows 10 专业版 1909

## uni-app运行环境说明

[运行端是h5或app或某个小程序？]

小程序

[运行端版本号]

Stable v1.02.2003250

[项目是cli创建的还是HBuilderX创建的？如果是cli创建的，请更新到最新版cli再试]

HBuilderX创建

[编译模式说明：自定义组件模式？纯nvue模式？v3模式？]

自定义组件模式

## 联系方式

[邮箱] yedsn@163.com