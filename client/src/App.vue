<template>
  <v-app>
    <LogoBar />
    <v-main>
      <v-container>
        <CarCards :cars="cars" />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import axios from 'axios';
import LogoBar from '@/components/LogoBar.vue';
import CarCards from '@/components/CarCards.vue';

export default {
  name: 'App',
  created() {
    this.getCars();
  },
  methods: {
    async getCars() {
      try {
        const { data } = await axios({
          url: 'http://127.0.0.1:3000/cars',
          method: 'GET',
        });
        this.cars = data;
      } catch (error) {
        console.error(error);
      }
    },
  },
  components: {
    LogoBar,
    CarCards,
  },
  data() {
    return {
      cars: [],
    };
  },
};
</script>
