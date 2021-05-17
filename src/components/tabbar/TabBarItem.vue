<template>
  <div class="tab-bar-item">
    <div v-if="!isActive" @click="itemClick">
      <slot name="item-icon"></slot>
    </div>
    <div v-else>
      <slot name="item-icon-active"></slot>
    </div>
    <slot name="item-text"></slot>

  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props:{
    path:String
  },
  data(){
    return{
      // isActive: true,
    }
  },
  computed:{
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1;
    }
  },
  methods:{
    itemClick() {
      // console.log('itemClick');
      this.$router.replace(this.path).catch(err=>{})
    }
  }
}
</script>

<style scoped>
.tab-bar-item {
  flex: 1;
  height: 49px;
  text-align: center;
  font-size: 14px;
}
.tab-bar-item img {
  width: 24px;
  height: 24px;
  vertical-align: middle;
  margin-top: 2px;
}
</style>
