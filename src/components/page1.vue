<template>
  <div>
    <div class="txtColor">{{page}}</div>
    <button @click="add()">点我</button>
    <child :message='value'></child>
    <ul>
      <li v-for="(item,index) in items" :key="item.id">{{item.name}} {{item.id}}</li>
    </ul>
    <span v-text="page"></span>
  </div>
</template>

<script>
  import ChildNode from './HelloWorld.vue';

  export default {
    data() {
      return {
        page: 'success',
        value: 2,
        items:[{name:"大连",id:3},{name:"大连",id:1},{name:"大连",id:2}]
      }
    },

    components: {
      child: ChildNode
    },
    methods: {
      add() {
        this.value+=1;
      }
    },
    beforeCreate() {
      // 开始监控data数据变化，初始化vue内部事件
      console.log('beforeCreate')
    },
    created() {
      // 编译模板，将data中的数据和模板生成html
      console.log('create')
    },
    beforeMount() {
      // 此时还没有生成html到页面中
      console.log('beforeMount')
    },
    mounted() {
      // 模板中的html渲染到页面中
      // 此时可以进行ajax操作
      // mounted 只会执行一次
      console.log('mounted')
    },
    beforeUpdate() {
      //更新之前的钩子函数
    },
    updated() {
      // 更新完成后的钩子
    },
    beforeDestroy() {
      // 实例销毁前
    },
    destroy() {
      // 实例被销毁
    }

  }
</script>
<style scoped>
  .txtColor {
    color: green
  }
</style>
