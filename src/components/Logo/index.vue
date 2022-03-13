<template>
  <div class="logo-container">
    <router-link class="logo-link" to="/">
      <img v-if="logo" :src="logo" class="logo">
      <h1 class="logo-title">{{ title }} </h1>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'Logo',
  data() {
    return {
      title: 'Vue Element Admin',
      logo: 'https://wpimg.wallstcn.com/69a1c46c-eb1c-4b46-8bd4-e9e686ef5251.png'
    }
  }
}
</script>

<style lang="scss">
.logo-container {
  position: relative;
  // width: 100%;
  height: 50px;
  line-height: 50px;
  text-align: center;

  .logo-link {
    display: inline-block;
    // width: 100%;
    height: 100%;
  }
  .logo {
    width: 32px;
    height: 32px;
  }
}
</style>
