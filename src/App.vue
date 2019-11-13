<template>
  <v-app id="app">
    <v-app-bar
      app
      color="#fdc0b0"
      dark
    >
      <v-spacer />
      <v-toolbar-title class="p-a-5">
        <Date />
      </v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container
        fluid
      >
        <v-row
          align="start"
          justify="start"
          class="mb-5"
        >
          <v-col><Visual /></v-col>
          <v-col><Todo /></v-col>
        </v-row>
        <v-row
          align="start"
          justify="center"
          class="mt-5"
        >
          <v-col><Feelings /></v-col>
          <v-col><Water /></v-col>
        </v-row>
      </v-container>
    </v-content>

    <v-footer
      color="#fdc0b0"
      app
      class="pa-5"
    >
      <v-spacer />
      <span class="time font-weight-bold">{{ moment().format('LT') }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import moment from 'moment'
// import vSelect from 'vue-select'
import Date from './components/Date'
import Visual from './components/Visual'
import Todo from './components/Todo'
import Water from './components/Water'
import Feelings from './components/Feelings'


  export default {
    name: 'LayoutsDemosBaselineFlipped',
    components: {
      Date,
      Visual,
      Todo,
      Water,
      Feelings
    },
    props: {
      source: String,
    },
    data: () => ({
    }),
    methods: {
      moment: function (date) {
          return moment(date);
      }
    }
  }
</script>

<style lang="scss">
@import "./styles/variables.scss";

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: $background;
}
.v-app-bar {
  box-shadow: none;
}
.time {
  color:$pinkDark;
}
</style>
