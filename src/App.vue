<template>
  <v-app>
    <v-container fluid fill-height>
      <DatePicker />
    </v-container>
  </v-app>
</template>

<script>
import DatePicker from './components/DatePicker/index.vue'

export default {
  name: 'App',

  data: () => ({
    //
  }),
  components:{
    DatePicker
  }
};
</script>
