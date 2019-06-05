<template>
  <v-app>
    <v-navigation-drawer absolute temporary v-model="showNav" class="hidden-md-and-up">
      <v-list>
        <v-list-tile v-for="(item, index) in dataForBtn" :key="index"  nuxt :to="item.rout">
          <v-list-tile-action>
            <v-icon> {{ item.icon }} </v-icon>
          </v-list-tile-action>
            <v-list-tile-content>
              {{ item.name }}
            </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar 
    color="primary" 
    dark
    src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"
    >
      <!-- <v-toolbar-side-icon @click="showNav = !showNav" class="hidden-md-and-up"></v-toolbar-side-icon> -->
      <v-toolbar-side-icon @click="showNav = !showNav" class="hidden-md-and-up"></v-toolbar-side-icon>
      <v-toolbar-title>Hello World</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn flat v-for="(item, index) in dataForBtn" :key="index" :to="item.rout">
          <v-icon left> {{ item.icon }} </v-icon>
           {{ item.name }} 
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
      <v-content>
        <nuxt />
      </v-content>
  </v-app>
</template>

<script>
export default {
  data(){
    return{
        showNav: false,
        dataForBtn:[
          {
            icon: 'home',
            name: 'Button 1',
            rout: '/btn1'
          },
          {
            icon: 'android',
            name: 'Button 2',
            rout: '/btn2'
          },
          {
            icon: 'backup',
            name: 'Button 3',
            rout: '/btn3'
          },
          {
            icon: 'build',
            name: 'Button 4',
            rout: '/btn4'
          },
          {
            icon: 'build',
            name: 'Button 5',
            rout: '/btn5'
          }
        ]
    }
  },
  components: {

  }
}
</script>
