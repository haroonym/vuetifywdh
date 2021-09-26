<template>
  <div class="d-flex flex-wrap justify-center">
    <CarCard :c="car" v-for="(car, i) of cars" :key="i" @reserved="reserved($event)" />
  </div>
</template>

<script>
import axios from 'axios';
import CarCard from '@/components/CarCard.vue';
export default {
  props: {
    cars: {
      type: Array,
    },
  },
  components: {
    CarCard,
  },
  methods: {
    async reserved(i) {
      try {
        await axios({
          url: `http://127.0.0.1:3000/cars/${i.id}`,
          method: 'PATCH',
          contentType: 'application/json',
          data: {
            title: `${i.title} RESERVED`,
          },
        });
        return this.$emit('reserved', true);
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
