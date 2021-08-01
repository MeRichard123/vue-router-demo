<template>
  <div id="nav">
    <!--
    the ui library lets me set router to true and it will pass the index to router-link
    <router-link to="/">Home</router-link>
    <router-link to="/about">About</router-link>
    without the ui library you would need the above.
    -->
    <router-link class="logo" :style="{'color': color}" to="/">TheGenericWebsite</router-link>
    <el-menu :default-active="activeIndex" class="el-menu-demo" router=true :text-color="color"
      :active-text-color="color" mode="horizontal" @select="handleSelect">
      <el-menu-item class="item" index="/">Home</el-menu-item >
      <el-menu-item class="item" index="about">About</el-menu-item>
      <el-menu-item class="item" index="contact">Contact</el-menu-item>
    </el-menu>
  </div>
  <!-- <p @click="goBack" class="button">Go Back</p> -->
  <router-view/>
</template>
<script>
export default {
  name: 'App',
  data() {
    return { color: '#fff' };
  },
  watch: {
    $route: 'logPath',
  },
  methods: {
    logPath() {
      console.log(this.$route.path);
      if (this.$route.path !== '/') {
        this.color = '#000';
      } else {
        this.color = '#fff';
      }
    },
    goBack() {
      return window.history.length > 1 ? this.$router.go(-1) : this.router.$push('/');
    },
  },
};
</script>

<style>
*{
  margin: 0;
}
.logo{
  height: 100%;
  text-decoration: none;
  padding: 0 20px;
  display: flex;
  align-items: center;
}
.button{
  cursor: pointer;
}
.el-menu--horizontal > .el-menu-item:not(.is-disabled):focus,
.el-menu--horizontal > .el-menu-item:not(.is-disabled):hover {
  background-color: hsl(1, 31%, 69%) !important;
}
.el-menu-demo{
  background: transparent !important;
}
#nav{
  display: grid;
  grid-template-columns: 1fr max-content;
  box-shadow: 0px 2px 1px -1px hsla(0, 0%, 0%, 0.15);
  margin: 0 12px;
  color: white;
  position: fixed;
  top: 0;
  width: 96vw
}
@media screen and (max-width: 900px){
  #nav{
    grid-template-columns: 1fr;
    grid-template-rows: repeat(2, 1fr);
    place-items: center;
    justify-content: center;
  }
}
</style>
