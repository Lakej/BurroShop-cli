<template>
  <v-app > 
    
    <!--Barra superior (Header)-->
    <v-toolbar color="guinda" dark app>
     <v-toolbar-side-icon v-if="!drawer"  @click="drawer = !drawer"></v-toolbar-side-icon>

      <router-link to="/" tag="span">
        <span class="title ml-3 mr-5">Burro&nbsp;<span class="font-weight-light">Shop</span></span>
      </router-link>
      <v-text-field
        solo-inverted
        flat
        hide-details
        label="Buscar"
        prepend-inner-icon="search"
      ></v-text-field>

    </v-toolbar>
    
    <!--Barra de Navegacion Lateral-->
    <v-navigation-drawer app v-model="drawer" :mini-variant.sync="mini" hide-overlay floating>
        <v-list class="pa-1" align-center>
        <v-list-tile avatar tag="div" align-center>
          <v-list-tile-avatar>
            <img src="./assets/ipnlog.png">
          </v-list-tile-avatar>



        <!--
         <v-list-tile avatar tag="div">
          <v-list-tile-avatar>
            <img src="./assets/bshoplog.png">
          </v-list-tile-avatar>

          <v-list-tile-content>
            <v-list-tile-title>{{usuario.nombre}}</v-list-tile-title>
          </v-list-tile-content>
          -->

          <v-list-tile-action>
            <v-btn icon @click.stop="mini = !mini">
              <v-icon>chevron_left</v-icon>
            </v-btn>
          </v-list-tile-action>
        </v-list-tile>
      </v-list>

      
      

      <v-list class="pt-0" dense >
        <v-divider></v-divider>

        <v-subheader class="mt-3 grey--text text--darken-1">CUENTA</v-subheader>

        <v-list-tile
            v-for="(perfil, i) in perfiles"
            :key="i"
            @click=""
            :to="perfil[2]"

          >
            <v-list-tile-action>
              <v-icon v-text="perfil[1]"></v-icon>
            </v-list-tile-action>
            <v-list-tile-title v-text="perfil[0]"></v-list-tile-title>
            
          </v-list-tile>

        <v-subheader class="mt-3 grey--text text--darken-1">PRODUCTOS</v-subheader>

        <!--Menu Comida-->
        <v-list-group prepend-icon="android" no-action sub-group>
          <template v-slot:activator>
            <v-list-tile>
              <v-list-tile-title>Comida</v-list-tile-title>
            </v-list-tile>
          </template>

          <v-list-tile
            v-for="(comida, i) in comidas"
            :key="i"
            @click=""

          >
            <v-list-tile-action>
              <v-icon v-text="comida[1]"></v-icon>
            </v-list-tile-action>
            <v-list-tile-title v-text="comida[0]"></v-list-tile-title>
            
          </v-list-tile>
        </v-list-group>
        
        <!--Menu Materiales-->
        <v-list-group sub-group no-action prepend-icon="android">
          <template v-slot:activator>
            <v-list-tile>
              <v-list-tile-title>Materiales</v-list-tile-title>
            </v-list-tile>
          </template>

          <v-list-tile
            v-for="(material, i) in materiales"
            :key="i"
            @click=""
          >
            <v-list-tile-action>
              <v-icon v-text="material[1]"></v-icon>
            </v-list-tile-action>
            <v-list-title v-text="material[0]"></v-list-title>
          </v-list-tile>
        </v-list-group>

        <!--Menu Libros-->
        <v-list-group sub-group no-action prepend-icon="android">
          <template v-slot:activator>
            <v-list-tile>
              <v-list-tile-title>Libros</v-list-tile-title>
            </v-list-tile>
          </template>

          <v-list-tile
            v-for="(libro, i) in libros"
            :key="i"
            @click=""
          >
          <v-list-tile-action>
            <v-icon v-text="libro[1]"></v-icon>
          </v-list-tile-action>
          <v-list-title v-text="libro[0]"></v-list-title>
          </v-list-tile>
        </v-list-group>

        <!--Menu Segunda Mano-->
        <v-list-group sub-group no-action prepend-icon="android">
          <template v-slot:activator>
            <v-list-tile>
              <v-list-tile-title>Segunda Mano</v-list-tile-title>
            </v-list-tile>
          </template>

          <v-list-tile
            v-for="(segunda, i) in segmano"
            :key="i"
            @click=""
          >
          <v-list-tile-action>
            <v-icon v-text="segunda[1]"></v-icon>
          </v-list-tile-action>
          <v-list-title v-text="segunda[0]"></v-list-title>
          </v-list-tile>
        </v-list-group>

        <!--Menu Renta-->
        <v-list-group sub-group no-action prepend-icon="android">
          <template v-slot:activator>
            <v-list-tile>
              <v-list-tile-title>Renta</v-list-tile-title>
            </v-list-tile>
          </template>

          <v-list-tile
            v-for="(renta, i) in rentas"
            :key="i"
            @click=""
          >
          <v-list-tile-action>
            <v-icon v-text="renta[1]"></v-icon>
          </v-list-tile-action>
          <v-list-title v-text="renta[0]"></v-list-title>
          </v-list-tile>
        </v-list-group>



        <!--<v-list-tile
          v-for="item in items"
          :key="item.title"
          @click=""
        >
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>

          <v-list-tile-content>
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>-->
      </v-list>
      
    </v-navigation-drawer>
    

    <v-content>
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>
  import finder from './components/finder.vue'
  import Firebase from 'firebase'
  import config from './config.js'

  let app = Firebase.initializeApp(config);
  let db = app.database();
  let usuariosRef = db.ref('usuarios');



export default {

  Firebase: {
    usuarios: usuariosRef
  },

  components:{
    finder
  },
  

  name: 'App',
  data () {
    return {  
      drawer: true,
      usuario: {nombre: 'Ricardo Garcia King'},
      perfiles: [
        ['Iniciar Sesion', 'android', '/'],
        ['Registrarse', 'android', '/registro']
      ],
      comidas: [
        ['Preparada', 'people_outline', '/'],
        ['Rápida', 'settings', '/'],
        ['Snacks', 'android', '/'],
        ['Bebidas', 'android', '/'],
        ['Botanas', 'android', '/']
      ],
      materiales: [
        ['Carreras', 'android', '/'],
        ['Otros', 'android', '/']
      ],
      libros: [
        ['Carreras', 'android', '/'],
        ['Básicas', 'android', '/'],
        ['Humanisticas', 'android', '/'],
        ['Otros', 'android', '/']
      ],
      segmano: [
        ['Laboratorio', 'android', '/'],
        ['Carreras', 'android', '/'],
        ['Dibujo', 'android', '/'],
        ['Miscelaneo', 'android', '/']
      ],
      rentas: [
        ['Laboratorio', 'android', '/'],
        ['Carreras', 'android', '/'],
        ['Dibujo', 'android', '/'],
        ['Miscelaneo', 'android', '/']
      ],
      mini: true,
      right: null,
      visible: false,

      newUser:{
        name: '',
        boleta: '',
        password: ''
      }
    }
  }
}
</script>
