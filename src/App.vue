<template>
<div class="switch" @click="handleClick">
  <span v-if="showDark">

  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
  <path fill-rule="evenodd" d="M10 2a1 1 0 011 1v1a1 1 0 11-2 0V3a1 1 0 011-1zm4 8a4 4 0 11-8 0 4 4 0 018 0zm-.464 4.95l.707.707a1 1 0 001.414-1.414l-.707-.707a1 1 0 00-1.414 1.414zm2.12-10.607a1 1 0 010 1.414l-.706.707a1 1 0 11-1.414-1.414l.707-.707a1 1 0 011.414 0zM17 11a1 1 0 100-2h-1a1 1 0 100 2h1zm-7 4a1 1 0 011 1v1a1 1 0 11-2 0v-1a1 1 0 011-1zM5.05 6.464A1 1 0 106.465 5.05l-.708-.707a1 1 0 00-1.414 1.414l.707.707zm1.414 8.486l-.707.707a1 1 0 01-1.414-1.414l.707-.707a1 1 0 011.414 1.414zM4 11a1 1 0 100-2H3a1 1 0 000 2h1z" clip-rule="evenodd" />
</svg>
</span>
<span v-else>
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
  <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z" />
</svg>
</span>
</div>
<span class="tag">{{tag}}</span>
<h1>{{headline}}</h1>
  <Cards />
</template>

<script>
import { ref } from '@vue/reactivity'
import Cards from './components/Cards.vue'

export default {
  name: 'App',
  components: {
    Cards
  },
  setup(){
     const tag = ref("Our team")
  const headline = ref("Meet our team")
  const showDark = ref(false)

  const handleClick = () =>{
    const body = document.querySelector("body")
    body.classList.toggle("isDark")
    showDark.value = !showDark.value
  }


  return{tag,headline,handleClick,showDark}
  }
}
</script>

<style>
*{
    padding: 0;
  box-sizing: border-box;
  margin: 0;
}
span{
  font-size: 1rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  color: #3778bc;
}

.switch{
  display: inline-block;
  position: absolute;
  top: 30px;
  right: 50px;
  }

.switch svg{
  width: 25px;
}

.switch span{
 cursor: pointer;
}

h1{
  margin: 0.15em 0 1.2em;
  font-size: 3.5rem;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 60px;
}

html,body{
      min-height: 100vh;
}
body{
background: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' version='1.1' xmlns:xlink='http://www.w3.org/1999/xlink' xmlns:svgjs='http://svgjs.com/svgjs' width='1920' height='1080' preserveAspectRatio='none' viewBox='0 0 1920 1080'%3e%3cg mask='url(%26quot%3b%23SvgjsMask1004%26quot%3b)' fill='none'%3e%3crect width='1920' height='1080' x='0' y='0' fill='rgba(255%2c 255%2c 255%2c 1)'%3e%3c/rect%3e%3cpath d='M97.51 1179.54C283.84 1160.41 399.67 761.36 717.97 759.54 1036.28 757.72 1028.2 894.54 1338.44 894.54 1648.67 894.54 1800.16 760.32 1958.9 759.54' stroke='rgba(51%2c121%2c194%2c0.58)' stroke-width='2'%3e%3c/path%3e%3cpath d='M432.73 1123.36C585.91 1111.13 691.25 804.49 957.82 803.79 1224.39 803.09 1220.37 938.79 1482.91 938.79 1745.45 938.79 1872.46 804.86 2008 803.79' stroke='rgba(51%2c121%2c194%2c0.58)' stroke-width='2'%3e%3c/path%3e%3cpath d='M750.02 1274.43C963.81 1244.55 1024.33 784.94 1431.91 744.71 1839.5 704.48 1919.29 379.07 2113.81 366.71' stroke='rgba(51%2c121%2c194%2c0.58)' stroke-width='2'%3e%3c/path%3e%3cpath d='M552.35 1119.45C711.25 1101.84 807.99 754.14 1076.28 752.76 1344.57 751.38 1338.25 887.76 1600.22 887.76 1862.18 887.76 1988.89 753.84 2124.15 752.76' stroke='rgba(51%2c121%2c194%2c0.58)' stroke-width='2'%3e%3c/path%3e%3cpath d='M697.53 1205.91C867.98 1133.77 798.95 603.74 1126.66 602.63 1454.37 601.52 1752.7 952.04 1984.92 959.03' stroke='rgba(51%2c121%2c194%2c0.58)' stroke-width='2'%3e%3c/path%3e%3c/g%3e%3cdefs%3e%3cmask id='SvgjsMask1004'%3e%3crect width='1920' height='1080' fill='white'%3e%3c/rect%3e%3c/mask%3e%3c/defs%3e%3c/svg%3e") no-repeat 50% 50%/cover;
  background-attachment: fixed;
  display: flex;
    flex-direction: column;
    justify-content: center;
}
</style>
