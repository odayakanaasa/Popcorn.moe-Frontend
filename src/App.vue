<template>
  <v-app :light="!darkTheme" :dark="darkTheme">
    <v-slide-x-transition mode="out-in">
      <auth-layout v-if="isAuth"></auth-layout>
      <layout v-else></layout>
    </v-slide-x-transition>
  </v-app>
</template>

<script>
  import { mapGetters } from 'vuex'
  import { VApp } from 'vuetify/es5/components'
  import { VSlideXTransition } from 'vuetify/es5/components/transitions'
  import Layout from './components/layout/Layout'
  import AuthLayout from './components/layout/AuthLayout'

  export default {
    components: {
      Layout,
      AuthLayout,
      VApp,
      VSlideXTransition
    },
    computed: {
      ...mapGetters({
        darkTheme: 'darkTheme',
      }),
      isAuth () {
        return this.$route.path.match('auth')
      }
    }
  }
</script>
