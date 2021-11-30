<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

<!--        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        /> -->
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="#"
        target="_self"
        text
      >
        <span class="mr-2">Contact Me</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <index/>
      <newCustom/>
    </v-main>
  </v-app>
</template>

<script>
    
 // import HelloWorld from './components/HelloWorld';
import newCustom from './components/newCustom.vue';
import index from './components/index.vue';

export default {
  name: 'App',

  components: {
    newCustom,
    index
	// HelloWorld
  },

  data: () => ({
    //
  }),
 created () {
      setTimeout(() => {
          window.L2Dwidget.init({
          pluginRootPath: 'static/live2dw/',
          pluginJsPath: 'lib/',
          pluginModelPath: 'live2d-widget-model-shizuku/assets/',
          tagMode: false,
          debug: false,
          model: { jsonPath: '../static/live2dw/live2d-widget-model-shizuku/assets/shizuku.model.json' },
          display: { position: 'right', width: 300, height: 650 },
          mobile: { show: true },
          log: false
          })
      }, 1000)
  },
};
</script>
