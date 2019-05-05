<template>
  <v-container grid-list-md text-xs-center>

    <!--Carousel-->
    <v-layout align-center justify-center row pb-5>
      <v-carousel>
        <v-carousel-item
          v-for="item in items"
          :src="item.src"
          :key="item.id"
        >
        <v-layout
          align-start 
          justify-end 
          column 
          fill-height 
          pa-3
          
        >
          <div class="title font-weight-light">{{item.texto}}</div>
        </v-layout>
        </v-carousel-item>
      </v-carousel>
    </v-layout>
   
    <v-layout row wrap>
      <v-flex v-for="i in 6" :key="i"  xs4>
        <v-card class="mx-auto" max-width="300" pt-5>
        <v-img :src="images.sample"
        >
          <v-layout
            align-end
            fill-height
            pa-2
          >
            <div class="title font-weight-light">Explora los nuevos productos</div>
          </v-layout>
        </v-img>
        <v-card-title>
          <div class="text-truncate">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Assumenda, facilis vitae. Quibusdam porro modi, nemo minus dolore nobis ipsa enim, placeat, laboriosam exercitationem totam architecto ab illo labore sed voluptatum.</div>
        </v-card-title>
        <v-spacer></v-spacer>
        <v-btn
          pa-5
          color="guinda"
          depressed
        >Explorar</v-btn>

      </v-card>
      </v-flex>
      
    </v-layout>


  </v-container>
</template>



<script>
  export default {
    data: () => ({
      images: 
      {
        sample: require('../assets/com.jpg')
      }
      , 
      items: [
          {
            src: 'https://previews.123rf.com/images/dolgachov/dolgachov1603/dolgachov160305233/55283534-comida-r%C3%A1pida-y-el-concepto-de-alimentaci%C3%B3n-poco-saludable-cerca-de-bocadillos-de-comida-r%C3%A1pida-y-refresco-.jpg',
            texto: 'Dulces y comida preparada',
            id: 1111111111
          },
          {
            src: 'http://www.expidetufactura.com.mx/blog/wp-content/uploads/2017/03/herramientas-digitales.jpg',
            texto: 'Material de trabajo',
            id: 2222222222
          },
          {
            src: 'https://ined21.com/wp-content/uploads/LOS-LIBROS-INED21.jpg',
            texto: 'Libros',
            id: 3333333333
          },
          {
            src: 'https://gananci.com/wp-content/uploads/2017/01/segunda-mano.jpg',
            texto: 'Segunda Mano',
            id: 4444444444
          }
        ]
    })
  }
</script>
