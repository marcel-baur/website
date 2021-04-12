<template>
    <div class="toggle" @click="toggleTheme">
       <img v-if="isDark" class='darkmode-icon' alt="MB" src="./assets/off.svg" />
       <img v-if="!isDark" class='darkmode-icon' alt="MB" src="./assets/on.svg" />
       </div>

  <div class="container">
  <img alt="MB" src="./assets/g.svg" />
  <Main msg="I'm Marcel Baur" />
</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Main from './components/Main.vue'
import themeChanger from './theme';

const routes = [
  { path: '/', component: Main },
  { path: '/projects', component: Main },
];

// @ts-ignore


export default defineComponent({
  name: 'App',
  components: {
    Main
  },
  data() {
    return {
      themeChanger: new themeChanger(),
      isDark: false,
    }
  },
  created() {
    this.themeChanger = new themeChanger();
  },
  methods: {
    toggleTheme() {
      this.themeChanger._darkThemeSwitch();
      this.isDark = !this.isDark;
    }
  }
})
</script>

<style>
  :root{
  --icon-size: 24px;
 } 
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
img {
  max-height: 360px;
  max-width: 360px;
}
.toggle {
  cursor: pointer;
  position: absolute;
  top: 12px;
  right: 12px;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 12px;
}
.darkmode-icon {
  height: var(--icon-size);
  width: var(--icon-size);
  max-height: var(--icon-size);
  max-width: var(--icon-size);
}
</style>