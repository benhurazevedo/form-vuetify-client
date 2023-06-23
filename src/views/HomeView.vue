<template>
  <v-form>
    <v-container>
      <v-row>
        <v-col
          cols="12"
          sm="6"
          md="4"
        >
          <v-text-field
            dense
            label="Digite o nome"
            v-model="nome"
          ></v-text-field>
          <v-btn
            color="primary"
            elevation="2"
            @click="enviar"
          >Envie</v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>
<script>
  import api from '../services/api'
  export default {
    name: 'Home',
    data: function(){
      return {
        nome: null
      }
    },
    methods:{
      enviar: function(){
        if(this.nome == null)
        {
          alert("preencha o campo!");
          return;
        }
        else if(this.nome.length == 0)
        {
          alert("preencha o campo!");
          return;
        }
        else 
        {
          //console.log(JSON.stringify({nome: this.nome}));
          api.post('/setnome',{nome: this.nome})
            .then((response) => {
              this.$router.push('/about');
            });
        }
      },
    },
  }
</script>
