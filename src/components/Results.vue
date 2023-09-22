<template>
  <p>Your Reaction Time is: {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  data() {
    return {
      rank: null,
    };
  },
  props: ["score"],
  mounted() {
    if (this.score < 200) {
      this.rank = "Ninja Fingers!";
    } else if (this.score < 400) {
      this.rank = "Rapid Reflexes!";
    } else {
      this.rank = "Slow as a snail!";
    }
  },
};
</script>

<style>
p {
  font-size: 22px;
  margin-top: 30px;
}
.rank {
  color: rgb(22, 187, 41);
  font-weight: bold;
  font-size: 40px;
}
</style>
