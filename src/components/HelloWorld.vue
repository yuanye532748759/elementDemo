<template>
  <div class="hello">
    <div class="tab">
      <div class="title-box">
        <div v-for="(item,index) in titleList" :class="{color:chooseIndex===index}" @click="choose(index)" :key="index" class="lpr-title">{{item}}</div>
      </div>
      <test v-if="show" :list="list"></test>
    </div>   
  </div>
</template>

<script>
import test from './test.vue'
export default {
  name: 'HelloWorld',
  components:{
    test
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      titleList: ['术语解释', '操作指南'],
      chooseIndex: 0,
      show: false,
      list: []
    }
  },
  methods: {
    choose (index) {
      console.log(index)
      if (index === 1) {
        this.show = true
        this.list = [{name: 'yy'}]
      } else {
        this.show = false
      }
      this.chooseIndex = index
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
    width: 100%;
    height: 100%;
}
.tab {
    width: 100%;
    height: 37px;
    line-height: 37px;
    box-sizing: border-box;
    border-bottom: 1px solid #cbcad7;
}
.title-box {
    display: -webkit-flex;
    display: flex;
    justify-content: space-between;
    width: 100%;
    box-sizing: border-box;
    padding-left: 31%;
    padding-right: 31%;
}
.lpr-title {
    font-family: PingFangSC-Medium;
    font-size: 13px;
    color: #666666;
    /* position: relative; */
}
.color {
    color: #e82e4a;
    transition: all 1s linear;
    position: relative;
    /* transition: color 1s linear; */
}

.color:after {
    position: absolute;
    display: block;
    /* height: 2px; */
    content: "";
    border: 1px solid #e82e4a;
    right: 0px;
    bottom: 0px;
    left: 0px;
    transition: all 1s linear;
}
</style>
