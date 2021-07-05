<template>
  <Step 
  />
  <MyScript />
</template>

<script>
// import { bus } from './main'
import Step from './components/Step.vue'
import MyScript from './script.js'
export default {
  name: 'App',
  components: {
    Step,
    MyScript
  },
  // created() {
  //   bus.$on('newData', this.Company)
  // },
}
</script>

<style>
* {
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
}

body {
  margin: 0px 0px 0px 0px;
  color: #211536;
  font-family: Montserrat;
}

a {
  text-decoration: none;
  cursor: pointer;
}

li {
  list-style-type: none;
}

.ibg {
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  position: relative;
}

.ibg img {
  width: 0;
  height: 0;
  position: absolute;
  top: 0;
  left: 0;
  opacity: 0;
  visibility: hidden;
}
</style>
