# mpvue
### 生命周期
#### 注意点：
- 不要在选项属性或回调上使用箭头函数，比如 created: () => console.log(this.a) 或 vm.$watch('a', newValue => this.myMethod())。因为箭头函数是和父级上下文绑定在一起的，this 不会是如你做预期的 Vue 实例，且 this.a 或 this.myMethod 也会是未定义的。

- 微信小程序的页面的 query 参数是通过 onLoad 获取的，mpvue 对此进行了优化，直接通过 this.$root.$mp.query 获取相应的参数数据，其调用需要在 onLoad 生命周期触发之后使用，比如 onShow 等，具体生命周期调用顺序，见下图。


![image](img/lifecycle.jpg)