<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click me
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    console.log("mounted");
    setTimeout(() => {
      console.log(this.delay);
      this.startTimer();
    }, this.delay);
  },
  unmounted() {
    console.log("unmounted!!!");
  },
  methods: {
    startTimer() {
      this.showBlock = true;
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      this.showBlock = false;
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>
<style>
.block {
  width: 400px;
  margin: 20px auto;
  text-align: center;
  padding: 100px 0;
  background: #f00;
  border-radius: 20px;
  color: #fff;
}
</style>
