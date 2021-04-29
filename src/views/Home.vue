<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome"/>
    <div>ip地址：{{ip}}</div>
    <div class="bottom">所在城市：{{city}}</div>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data() {
    return {
      ip: "",
      city: ""
    }
  },
  created() {
    this.getYourIp();
  },
  methods: {
    async getYourIp() {
      const res = await fetch("https://ipapi.co/json/").then(x => x.json());
      console.log(res)
      this.ip = res.ip;
      this.city = res.city;
    }
  }
}
</script>

<style lang="less" scoped>
  .bottom{
    border-bottom: 1px solid #eee;
    padding-bottom: 10px;
  }
</style>
