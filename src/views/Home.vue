<template>
  <div>
   <div class="topnavAndBanner">
     <Topnav/>
     <div class="banner">
       <h1>Vue 轮子UI</h1>
       <p class="actions">
         <a>Github</a>
         <router-link to="/doc">开始</router-link>
       </p>
     </div>
   </div>
   <div class="features">
     <ul>
       <li>
         <svg>
           <use xlink:href="#icon-vue"></use>
         </svg>
         <h3>基于 Vue 3</h3>
         <p>骄傲地使用了 Vue 3 Composition API</p>
       </li>
       <li>
         <svg>
           <use xlink:href="#icon-ts"></use>
         </svg>
         <h3>基于 TypeScript </h3>
         <p>源代码采用 TypeScript 书写（非严格检查）</p>
       </li>
       <li>
         <svg>
           <use xlink:href="#icon-light"></use>
         </svg>
         <h3>代码易读</h3>
         <p>每个组件的源代码都极其简洁</p>
       </li>
     </ul>
   </div>
  </div>
</template>

<script lang="ts">
  import Topnav from "../components/Topnav.vue"
  export default {
  components: {Topnav}
};
</script>
<style lang="scss" scoped>
.topnavAndBanner{
  background-image: url("../assets/bg.jpg");
  clip-path: ellipse(80% 60% at 50% 40%);
}
.features {
  margin: 64px auto;
  width: 400px;
  color: black;
  @media (min-width: 800px) {
    width: 800px;
  }
  @media (min-width: 1200px) {
    width: 1200px;
  }
  >ul {
    display: flex;
    flex-wrap: wrap;
    >li {
      width: 400px;
      margin: 16px 0;
      display: grid;
      justify-content: start;
      align-content: space-between;
      grid-template-areas:
        "icon title"
        "icon text";
      grid-template-columns: 80px auto;
      grid-template-rows: 1fr auto;
      >svg {
        grid-area: icon;
        width: 64px;
        height: 64px;
      }
      >h3 {
        grid-area: title;
        font-size: 28px;
      }
      >p {
        grid-area: text
      }
    }
}
}
.banner {
  padding: 200px 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  > .actions{
    padding: 26px 0;
    a {
      margin:0 8px;
      display: inline-block;
      border-radius: 4px;
      padding: 8px 24px;
      border: 1px solid #b1b3b4;
      background-color:rgba(255,255,255,0.1);
    }
    a:hover {
      background-color: #d43540;
    }
  }
}
</style>
