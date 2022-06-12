<template>
 <CardDetail v-if="showModal" @close="toggleModal" :person="person"/>
  <div class="card" @click="toggleModal" :class="showModal ? 'active' : ''">
      <div class="card-img">
          <img :src="person?.picture.large" alt="">
      </div>
      <h2>{{person?.name.first + " " + person?.name.last}}</h2>
      <a>{{person?.email}}</a>
  </div>

</template>

<script>
import CardDetail from '@/components/CardDetail.vue'
import { ref } from '@vue/reactivity'
export default {
props:["person"],
components:{CardDetail},
setup(){
       const showModal = ref(false)
    const toggleModal = () =>{
    showModal.value = !showModal.value
    }

    return{toggleModal,showModal}
}
}
</script>

<style scoped>
h2{
        margin: 0.8em 0 0.4em;
}
.card{
background:#fff;
box-shadow: 6px 5px 20px #d3e8ff;
cursor: pointer;
padding: 30px;
border-radius: 0.4em;
transition: box-shadow 0.3s ease-in-out;

}
.card:hover, .card.active{
    box-shadow: 6px 5px 18px #b3cde8;
}

.card:hover a,.card.active a{
text-decoration: underline;
color: #2a5b8d;
}

.card:hover img,.card.active img{
    transform: scale(1.1) rotate(3deg);
}

.card-img{
    aspect-ratio: 1/1;
    overflow: hidden;
    border-radius: 0.3em;

}
.card img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: 0.2s;
}

</style>