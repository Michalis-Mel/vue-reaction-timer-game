<template>
  <div v-if="showBlock" class="block" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  props: ["delay"],
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 90%;
  height: 300px;
  background: rgb(26, 115, 156);
  margin: 60px auto;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 40px;
  border-radius: 50px;
  cursor: pointer;
}
</style>
