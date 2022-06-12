<template>

<div class="grid">
  <TransitionGroup name="list">
    <div v-for="(person,index) in visibleTeam" :key="index" >
      <Card :person="person"/>
    </div>
  </TransitionGroup>
  <div v-if="error">
  {{error}}
  </div>
  <div v-if="loading">
    Loading...
  </div>
</div>

  <button @click="handleClick" v-if="isBtnVisible">Show more</button>
</template>

<script>
import Card from '@/components/Card.vue'
import { ref } from '@vue/reactivity'
import { computed } from '@vue/runtime-core'


export default {
  name: 'Cards',
  components: {Card},
  setup(){
  
    const visibleNumber = ref(3)
    const numberToIncrease = 3
    const showMore = ref(true)
    const loading = ref(false)

    const handleClick = () =>{
      visibleNumber.value += numberToIncrease

    }

     const team = ref([])
     const error = ref(null)

    const load = async () =>{
      try{
        loading.value = true
        let data = await fetch("https://randomuser.me/api/?results=20")
        if(!data.ok){
          throw Error("no data available")
        }
        
       
  
        team.value = await data.json().then(x=>x.results)
        loading.value = false
      }

      catch(err){
        loading.value = false
         error.value = err.message
      }
    }

load()

    const visibleTeam = computed(()=>{
      if(!team.value.length){
        return []
      }
    return team.value.slice(0,visibleNumber.value)
    })

    const isBtnVisible = computed(()=>{
    return visibleNumber.value < team.value.length 
    })

    return{team,visibleTeam,showMore,handleClick,isBtnVisible,error,loading}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.grid{
  max-width: 1200px;
  margin:0 auto;
  display: grid;
grid-template-columns:repeat(auto-fit,minmax(min(300px,100%),1fr));
gap: 30px;
}
button{
  display: inline-block;
  margin: 5em 0 0;
  background: #2a5b8d;
  color: #fff;
  border-radius: 0.4em;
  cursor: pointer;
  outline: none;
  border: none;
  padding: 1em 2.5em;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  font-weight: 700;
}

button:hover{
    background: #193e63;
}
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translatey(-30px);
}

.card2{
  width: 300px;
  display: flex;
}
</style>
