<template>
  <h1>{{ msg }}</h1>

  <p>
    Work:
    <a href="https://www.tawny.ai/" target="_blank">TAWNY GmbH</a> <br />
    Study:
    <a
      href="https://www.ifi.lmu.de"
      target="_blank"
    >Computer Science at University of Munich</a>
    
  </p>

  <p>Refer to my <a href="https://www.github.com/marcel-baur">GitHub</a> for personal projects.</p>
</template>

<script lang="ts">
  import themeChanger from '../theme';
  import { ref, defineComponent } from 'vue';

  export default defineComponent({
    name: 'HelloWorld',
    props: {
      msg: {
        type: String,
        required: true
      },
    },
    data() {
      return {
        message: "You opened the component at " + new Date().toLocaleDateString(),
        counter: 0,
        themeChanger: new themeChanger(),
      }
    },
    created() {
      this.themeChanger = new themeChanger();
    },
    setup: () => {
      const count = ref(0)
      return { count }
    },
    methods: {
      switchTheme() {
        this.themeChanger._darkThemeSwitch();
      }, 
      click(event: any) {
        this.message = "Changed the component at " + new Date().toLocaleDateString();
        this.counter++;
      }
    }
  })
</script>

<style scoped>
h2 {
  color: #42b983;
}

a {
  color: #f98125
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
