<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h2>O seu nome é: {{ nome }}</h2>
  </div>
</template>
<script>
import api from '../services/api'
export default {
  name: 'about',
  data: function(){
    return {
      nome: null
    };
  },
  mounted(){
    api.get('/getnome')
      .then((response) => {
        return response.data;
      })
      .then((data) =>{
        this.nome = data.nome;
      })
  },
}
</script>
