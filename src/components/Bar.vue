<template>
  <div class='bar' ref='bar'>
    <div class='blackLine line' v-bind:style="{ width: lineWidth(this.ranges[0]) }"></div>
    <div class='blueLine line' v-bind:style="{ width: lineWidth(this.ranges[1]) }"></div>
    <div class='lightBlueLine line' v-bind:style="{ width: lineWidth(this.ranges[2]) }"></div>
    <div class='arrow' ref='arrow'>
      <img src='./../assets/arrow.png'>
    </div>
    <div class="dottedLine" ref="dotted">
      <div></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Bar',
  data() {
    return {
      itemSize: 1,
      width: 0,
    };
  },
  /*  watch: {
    win: function FractiOnSize() {
      const win = document.documentElement.clientWidth;
      console.log(this.win);
      if (win < 850 && win > 700) {
        this.itemSize = 0.81;
      }

      if (win < 700 && win > 600) {
        this.itemSize = 0.61;
      }

      if (win < 600 && win > 500) {
        this.itemSize = 0.65;
      }

      if (win < 500 && win > 390) {
        this.itemSize = 0.5;
      }

      if (win < 390 && win > 260) {
        this.itemSize = 0.36;
      }
    },
  }, */
  methods: {
    FractiOnSize() {
      const win = document.documentElement.clientWidth;

      if (win < 850 && win > 700) {
        this.itemSize = 0.81;
      }

      if (win < 700 && win > 600) {
        this.itemSize = 0.61;
      }

      if (win < 600 && win > 500) {
        this.itemSize = 0.65;
      }

      if (win < 500 && win > 390) {
        this.itemSize = 0.5;
      }

      if (win < 390 && win > 260) {
        this.itemSize = 0.36;
      }
      const barWidth = this.$refs.bar.clientWidth - 30;
      const paddingInPercent = this.forecast / this.sumOfRanges;
      const padding = barWidth * paddingInPercent * this.itemSize;

      const { arrow } = this.$refs;
      const { dotted } = this.$refs;

      arrow.style.paddingLeft = `${padding}px`;
      dotted.style.width = `${padding}px`;
      console.log(this.itemSize);
    },

    lineWidth(range) {
      const width = (range / this.sumOfRanges) * 100;
      return `${width}%`;
    },
  },

  computed: {
    sumOfRanges() {
      return this.ranges.reduce((a, b) => a + b);
    },
  },

  created() {
    window.addEventListener('resize', this.FractiOnSize);
    window.addEventListener('resize', this.mounted);
    // eslint-disable-next-line no-unused-expressions
    this.FractiOnSize();
  },

  beforeDestroy() {
    window.removeEventListener('resize', this.FractiOnSize);
  },

  mounted() {
    // eslint-disable-next-line no-unused-expressions
    const barWidth = this.$refs.bar.clientWidth - 30;
    const paddingInPercent = this.forecast / this.sumOfRanges;
    const padding = barWidth * paddingInPercent * this.itemSize;

    const { arrow } = this.$refs;
    const { dotted } = this.$refs;
    arrow.style.paddingLeft = `${padding}px`;
    dotted.style.width = `${padding}px`;
  },
  props: ['ranges', 'forecast'],
};
</script>

<style scoped lang="scss">
.bar {
  height: 35px;
  width: 722px;
  border-radius: 15px;
  display: flex;
  overflow: hidden;
  .line {
    height: 100%;
  }
  .blackLine {
    background-color: #0b2034;
  }
  .blueLine {
    background-color: #256bff;
  }
  .lightBlueLine {
    background-color: #77c2f7;
  }
  .arrow {
    height: 35px;
    position: absolute;
    display: flex;
    align-items: center;
    > img {
      height: 22px;
      width: 22px;
      z-index: 2;
      transform: rotate(45deg);
    }
  }
  .dottedLine {
    height: 16px;
    position: absolute;
    display: flex;
    align-items: center;
    z-index: 3;
    border-bottom: 3px dashed #ffffff;
  }
  @media only screen and (max-width: 850px) {
    width: 586px;
  }
  @media only screen and (max-width: 700px) {
    width: 446px;
  }
  @media only screen and (max-width: 600px) {
    width: 470px;
    border-radius: 5px;
  }
  @media only screen and (max-width: 500px) {
    width: 360px;
  }
  @media only screen and (max-width: 390px) {
    width: 260px;
  }
}
</style>
