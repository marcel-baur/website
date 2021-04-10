<template>
    <div class="toggle" @click="toggleTheme">{{isDark? "💡" : "🌑"}}</div>

  <div class="container">
  <img alt="MB" src="./assets/Logo-clear.svg" />
  <Main msg="I'm Marcel Baur" />
</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Main from './components/Main.vue'
import themeChanger from './theme';

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
</style>