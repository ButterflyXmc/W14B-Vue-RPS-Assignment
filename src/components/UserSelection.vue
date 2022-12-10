<template>
  <div>
    <img @click="getRock" :src="rock.image" alt="rock" />
    <img @click="getPaper" :src="paper.image" alt="paper" />
    <img @click="getScissors" :src="scissors.image" alt="scissors" />
  </div>
</template>

<script>
export default {
  name: "UserSelection",
  data() {
    return {
      rock: {
        image:
          "https://i0.wp.com/wrpsa.com/wp-content/uploads/2021/08/rock.png?resize=413%2C386&ssl=1",
      },
      paper: {
        image:
          "https://i0.wp.com/wrpsa.com/wp-content/uploads/2021/08/paper.png?resize=413%2C386&ssl=1",
      },
      scissors: {
        image:
          "https://i0.wp.com/wrpsa.com/wp-content/uploads/2021/08/scissors.png?resize=413%2C386&ssl=1",
      },
    };
  },
  methods: {
    getRock() {
      this.$root.$emit(`userSelection`, this.rock.image);
    },
    getPaper() {
      this.$root.$emit(`userSelection`, this.paper.image);
    },
    getScissors() {
      this.$root.$emit(`userSelection`, this.scissors.image);
    },
  },
};
</script>

<style scoped>
</style>