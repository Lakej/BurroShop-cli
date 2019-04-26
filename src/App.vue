<template>
  <v-app dark> 
    
    <v-toolbar color="guinda" dark app>
     <v-toolbar-side-icon v-if="!drawer" @click="drawer = !drawer"></v-toolbar-side-icon>

      <span class="title ml-3 mr-5">Burro&nbsp;<span class="font-weight-light">Shop</span></span>
      <v-text-field
        solo-inverted
        flat
        hide-details
        label="Buscar"
        prepend-inner-icon="search"
      ></v-text-field>

    </v-toolbar>
    

    <v-navigation-drawer
      app
      v-model="drawer"
      :mini-variant="mini"
      dark
      
    >
        <v-list class="pa-1" align-center>
          <v-list-tile v-if="mini" @click.stop="mini = !mini">
            <v-list-tile-action>
              <v-icon>chevron_right</v-icon>
            </v-list-tile-action>
        </v-list-tile>

         <v-list-tile avatar tag="div">
          <v-list-tile-avatar>
            <img src="./assets/bshoplog.png">
          </v-list-tile-avatar>

          <v-list-tile-content>
            <v-list-tile-title>Ricardo Garcia</v-list-tile-title>
          </v-list-tile-content>

          <v-list-tile-action>
            <v-btn icon @click.stop="mini = !mini">
              <v-icon>chevron_left</v-icon>
            </v-btn>
          </v-list-tile-action>
        </v-list-tile>
      </v-list>

      <v-list class="pt-0" dense >
        <v-divider dark></v-divider>

        <v-list-tile
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
        </v-list-tile>
      </v-list>
      
    </v-navigation-drawer>
    

    <v-content>
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>
  import finder from './components/finder.vue'


export default {

  components:{
    finder
  },

  name: 'App',
  data () {
    return {  
      drawer: true,
      items: [
        { title: 'Principal', icon: 'whatshot'},
        { title: 'Acerca', icon: 'school' },
        { divider: true},
        { title: 'Cuenta', icon: 'person'}
      ],
      mini: true,
      right: null,
      visible: false
    }
  }
}
</script>
