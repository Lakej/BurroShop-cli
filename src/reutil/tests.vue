<v-layout>
    <!--Header-->
    <v-toolbar color="guinda" dark app>
        <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon>

      <span class="title ml-3 mr-5">Burro&nbsp;<span class="font-weight-light">Shop</span></span>
      
      <v-spacer></v-spacer>

      <v-text-field
          solo-inverted
          flat
          hide-details
          label="Buscar"
          prepend-inner-icon="search"
        ></v-text-field>
      
    </v-toolbar>

    <!--<v-layout justify-center column>
      
         
      <v-btn flat>
            Ingresar &nbsp;
            <v-icon>account_circle</v-icon>
          </v-btn>

      
    </v-layout>-->



    <!--Barra de Navegacion Lateral-->
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="mini"
      absolute
      temporary
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


        <!--<v-layout mt-4 column align-center>
          <v-flex>
            <v-avatar>
              <v-icon dark>person</v-icon>
            </v-avatar>
          </v-flex>
          <v-flex class="white--text mt-3 headline">
            Ricardo Garcia
          </v-flex>
        </v-layout>-->
    </v-navigation-drawer>
    </v-layout>