<template>
  <div style="margin-top:250px">
    <v-card class="mx-auto" max-width="375">
      <v-img height="300px" :src="c.image"></v-img>

      <v-card-title>{{ c.title }}</v-card-title>

      <v-card-text class="black--text">
        <p>
          Owner: <b>{{ c.owner.firstName }} {{ c.owner.lastName }}</b>
        </p>
        <p>
          Year: <b>{{ c.yearOfMake }}</b>
        </p>
        <span>
          Miles: <b>{{ c.miles }}</b>
        </span>
        <p>
          Price: <b>{{ c.price }}</b>
        </p>
        <p>
          {{ c.description }}
        </p>
      </v-card-text>

      <v-card-actions
        ><v-btn class="red darken-4" color="white" text @click="$emit('reserved', c)">
          BUY CAR
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  props: {
    c: {
      type: Object,
    },
  },
};
</script>

<style lang="scss" scoped></style>
