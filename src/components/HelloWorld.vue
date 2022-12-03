<template>
  <div class="hello">
    <h1>TEST GITHUB PAGES HI Bi <span> {{ changed }}</span></h1>
    <button @click="onChange" >INCREASE</button>
    <button @click="callOuput">CALL API</button>
    <h1>{{ output.app_name }}</h1>
  </div>
</template>

<script>
import { ref } from 'vue'
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  setup() {
    const changed = ref(0)
    const output = ref('')

    const onChange = () => {
      changed.value += 1
    }
    async function callOuput() {
      const res = await axios.get(
        'https://random-data-api.com/api/app/random_app'
      )
      output.value = res.data
    }
    return {
      changed,
      output,
      onChange,
      callOuput,
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
