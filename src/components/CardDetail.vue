<template>
<div class="backdrop" @click.self="closeModal">
    <div class="modal">
          <h3>About me</h3>
          <span>Location:</span>

        {{person.location.street.number}} {{person.location.street.name}}, {{person.location.city}} - {{person.location.state}}
        <br/>
  <span>Phone:</span>
{{person.phone}}
   <br/>
  <span>Username:</span>
{{person.login.username}}

    </div>
</div>
</template>

<script>
export default {
props:["person"],
methods:{
    closeModal(){
        this.$emit("close")
    }
}
}

</script>

<style>
.modal{
    max-width: 600px;
    padding: 30px;
    margin: 100px auto;
    background: #fff;
    border-radius: 10px;
    text-align: left;
    width: 100%;
}

h3{
    margin-bottom: 20px;
    font-size: 2rem;
}

span{
    margin-block: 10px;
    display: inline-block;
}

.backdrop{
    position: fixed;
    background: rgba(0,0,0,0.6);
    width: 100%;
    height: 100%;
    inset: 0;
    z-index: 9999;
    padding: 20px;
    display: flex;
    align-items: center;
}
</style>