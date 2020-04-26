<template>
	<view>
		{{pageValue}}
		{{getMethodValue()}}
		<slot-component>
			<template v-slot="{componentValue}">
				{{pageValue}}
				{{getMethodValue()}}
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
		},
		methods: {
			getMethodValue() {
				return '我是方法返回的值'
			}
		}
	}
</script>
