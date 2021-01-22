#  生命周期
1. beforeCreate: 在实例初始化之后，数据观测（data observer）和 event/watcher 事件配置之前被调用
2. created
-  在实例创建完成后被立即调用。
-  在这一步，实例已完成以下的配置：数据观测（data oberver），属性和方法的运算，watch/event 事件回调
-  然而，挂载阶段还未开始， $el 属性目前不可见
3. beforeMount：在挂在开始之前被调用：相关的渲染函数首次被调用
4. mounted：el 被新创建的 vm.$el 替换，挂载成功
5. beforeUpdate：数据更新之前调用
6. updated：组件DOM已经更新，组件更新完毕