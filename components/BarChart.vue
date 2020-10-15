<template>
  <div class="wrapper">
    <div class="col">
      <p v-for="score in scores" :key="score">{{ score }}</p>
    </div>
    <div class="chart">
      <div class="chart__bar" v-for="sub in data" :key="sub.name" :style="setStyle(sub)">
        <p>{{ sub.value }}</p>
      </div>
    </div>
    <div class="corner"></div>
    <div class="row">
      <div class="row__sub" v-for="sub in data" :key="sub.name" :style="setRowStyle()">
        {{ sub.name }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
    },
  },
  data() {
    return {
      scores: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    };
  },
  methods: {
    setStyle(sub) {
      return "height:" + (sub.value > 0 ? sub.value * 2 + "em" : "1px") + "; background-color:" + sub.color;
    },
    setRowStyle() {
      return "width:" + 100/this.data.length + "%";
    }
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  margin-left: 20px;
  width: 500px;
  display: inline-grid;
  grid-template-columns: 2em auto;
  gap: 1em;
}

.col {
  display: flex;
  flex-direction: column-reverse;
  text-align: right;

  p {
    position: relative;
    top: 1.3em;
    height: 2em;
  }
}

.row {
  display: flex;
  &__sub {
    text-align: center;
  }
}

.chart {
  border-left: solid 1px black;
  border-bottom: solid 1px black;

  background-size: 2em 2em;
  background-image: linear-gradient(to top, gray 1px, transparent 1px);

  display: flex;
  align-items: flex-end;
  justify-content: space-around;
  
    &__bar {
      width: 2em;
      text-align: center;
      p {
        position: relative;
        top: -1.2em;
      }
    }
}
</style>