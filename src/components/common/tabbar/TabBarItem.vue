<template>
  <div class="tab-bar-item" @click="itemclick">
    <div v-if="!isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
    
    <div :style="activeStyle"><slot name="item-text"></slot>   </div>
    
  </div>
</template>

<script>
export default {
  name:'TabBarItem',
  props: {
    path:String,
    activeColor:{
      type:String,
      default:'red'
    }
  },
  data() {
    return {
      // isActive:true

    }
  },
  computed: {
    isActive(){
      return this.$route.path.indexOf(this.path) !==-1
      // if (this.$route.path == this.path) {
      //   return true
      // }
      // else{
      //   return false
      // }

    },
    activeStyle(){
      return this.isActive ? {color: this.activeColor} : {}
    }
  },
  methods: {
    itemclick(){
      // this.$router.replace(this.path);
      this.$router.currentRoute.path == this.path || this.$router.replace(this.path);
      console.log(this.$route.path)

    }

  },
  components: {

  }
}
</script>

<style scoped>
  .tab-bar-item{
    flex: 1;
    text-align: center;
    height: 49px;
    /* line-height: 25px; */
    /* line-height: 49px; */
    font-size: 14px;
  }

  .tab-bar-item img{
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: middle;
    margin-bottom: 2px;

  }

  /* .active{
    color: red;
  } */

</style>
