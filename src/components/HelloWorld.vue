<template>
  <v-container grid-list-md text-xs-center>
    <v-layout row wrap>
     <v-flex xs4 v-for='element in menu' :key='element.id' :element='element'>
      <v-hover>
      <v-card class="card-pizzita">
        <v-img
          v-bind:src=element.imagen
          height="200px"
          class="pizzita-img"
        >
        </v-img>

          <v-card-title primary-title>
            <div>
              <div class="headline">{{ element.nombre_pizza }}</div>
              <span class="green--text">$ {{ element.precio }}</span>
            </div>
          </v-card-title>

          <v-card-text>{{ element.descripcion }}</v-card-text>
          <v-btn color="blue" :to="{name:'order',params: {id: element.id}}">Ordenar</v-btn>
        </v-card>
       </v-hover>
    </v-flex>
  </v-layout>
  </v-container>
</template>

<script>
  export default {
    data: () => ({
      show: false,
      menu: [],
      element: {
        id: null,
        nombre_pizza: null,
        descripcion: null,
        imagen: null,
        precio: null
      }
    }),
    created (){
      this.loadMenuPizzas()
    },
    methods: {
      loadMenuPizzas(){
        this.$axios.get('http://127.0.0.1:8000/api/v1/pizzas/menu')
        .then(
          menu => {
            this.menu = menu.data['menu']
          }
        )
      }
    }
  }
</script>

<style>

.card-pizzita {
  border-radius: 5% 5% 0 0%;
  margin-bottom: 10%;
  transition: transform .3s;
}

.card-pizzita:hover {
transform: scale(1.05);
}

.pizzita-img {
  border-radius: 100%;
  width: 70%;
  height: 70%;
  margin: 0 auto;
  /* top: 50px; */
}

</style>
