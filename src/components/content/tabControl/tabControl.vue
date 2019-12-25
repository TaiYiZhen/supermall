<template>
  <div class="tab-control">
    <div v-for="(item,index) in titles" class="tab-control-item"
    :class="{active:index==currentIndex}"
    @click="itemclick(index)" :key="item.name">
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: "tabControl",
    props: {
      titles: {
        type: Array,
        default () {
          return []
        }
      }
    },
    data() {
      return {
        currentIndex: 0
      }
    },
    methods:{
      itemclick(index){
        this.currentIndex=index;
      }
    }
  }
</script>

<style scoped>
  .tab-control {
    display: flex;
    text-align: center;
    font-size: 15px;
    height: 40px;
    line-height: 40px;
    background-color: white;
  }

  .tab-control-item {
    flex: 1;
  }

  .tab-control-item span{
    padding: 5px;
  }

  .active {
    color: hotpink;

  }

  .active span{
    border-bottom: 2px solid hotpink;

  }
</style>
