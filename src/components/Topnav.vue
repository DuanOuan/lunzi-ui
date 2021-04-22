<template>
  <div class="topnav">
    <router-link to="/" class="logo">
      <svg class="icon">
        <use xlink:href="#icon-home"></use>
      </svg>
    </router-link>
    <div v-if="toggleAsideButtonVisible" class="wrap" :class="{checked}" @click="toggle">
        <span></span>
        <span></span>
        <span></span>
    </div>
    <ul class="menu">
      <li>Github</li>
      <router-link to="/doc">文档</router-link>
    </ul>
  </div>
</template>

<script lang="ts">
  import { inject, Ref, ref } from 'vue'

  export default {
    props: {
      toggleAsideButtonVisible: {
        type: Boolean,
        default: false
      }
    },
    setup(){
      const asideVisible = inject<Ref<boolean>>('asideVisible')
      const checked = ref(false)
      const toggle = () => {
        checked.value = !checked.value
        asideVisible.value = !asideVisible.value
      }
      return { checked, toggle, asideVisible }
    }
  }
</script>

<style lang="scss">
  .topnav{
    display: flex;
    padding: 16px;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 20;
    justify-content: center;
    align-items: center;
    > .logo {
      padding-left: 20px;
      padding-top: 10px;
      margin-right: auto;
      transition: 1s ease;
      > svg{
        width: 40px;
        height: 40px;
      }
    }
    > .logo:hover {
      transform: scale(2);
    }
    > .menu {
       display: flex;
       white-space: nowrap;
       flex-wrap: nowrap;
       color: white;
       > li {
         margin: 0 1em;
       }
     }
    >.wrap{
      height: 46px;
      position: absolute;
      padding-top: 4px;
      cursor: pointer;
      left: 36px;
      display: none;
      > span {
        height: 4px;
        width: 34px;
        display: block;
        margin: 6px;
        position: relative;
        background-color: #fff;
        transition: 0.5s;
      }
    }
    @media (max-width: 500px) {
      > .menu{display: none;}
      > .logo{margin: 0 auto;}
      > .wrap{display: inline-block;}
    }
  }
  .wrap.checked span:nth-of-type(1){
    transform: translateY(10px) rotate(45deg);
  }
  .wrap.checked span:nth-of-type(2) {
    opacity: 0;
  }
  .wrap.checked span:nth-of-type(3) {
    transform: translateY(-10px) rotate(-45deg);
  }

</style>