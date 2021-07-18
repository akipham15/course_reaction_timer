<template>
  <p class="score">Score - {{ score }}</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    console.log("Result mounted!");
    this.showRank();
  },
  methods: {
    showRank() {
      if (this.score < 500) {
        this.rank = "Excilent!!!";
      } else {
        this.rank = "Slow hand!";
      }
      console.log(this.score);
      console.log(this.rank);
    },
  },
};
</script>
<style>
.rank {
  color: #0faf87;
  font-size: 1.4rem;
}
.score {
  display: inline-block;
  color: #ff7300;
  border-bottom: 1px solid #ff7300;
}
</style>
