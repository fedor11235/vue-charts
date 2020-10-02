<template>
    <div class="main">
        <div class="header">
            <div class="title">forecasts</div>
        </div>

        <div class="chart">
            <div class="chartsList">
                <div class="chartItem" v-for="chart in dataSet" :key="chart.title">
                    <Row :chart="chart" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Row from '@/components/Row.vue';

export default {
  data() {
    return {
      dataSet: [
        {
          title: 'Current Month',
          ranges: [10, 10, 10],
          forecast: 20,
          minValue: '1.6k',
          maxValue: '2.4k',
        },
        {
          title: 'Current Quarter',
          ranges: [20, 10, 40],
          forecast: 18,
          minValue: '1.6k',
          maxValue: '2.4k',
        },
      ],
    };
  },
  components: {
    Row,
  },
};
</script>

<style  scoped lang="scss">

@import url("https://fonts.googleapis.com/css2?family=Roboto&display=swap");

.main {
  width: 816px;
  background-color: #ffffff;
  border-radius: 20px;
  font-family: "Roboto", sans-serif;
  box-shadow: 0 0 2px rgba(0,0,0,0.5);

  .header {
    min-height: 83px;
    border-bottom: 1px #e8e9ea solid;
    padding: 0 30px;
    display: flex;
    justify-content: start;
    align-items: center;
    .title {
      text-transform: uppercase;
    }
    @media only screen and (max-width: 700px) {
      padding: 0 10px;
      min-height: 43px;
    }
  }
  .chart {
    .chartsList {
      padding: 0 47px;
      margin: 0;
      .listItem {
        list-style-type: none;
      }
      @media only screen and (max-width: 700px) {
        padding: 0 17px;
      }
      @media only screen and (max-width: 600px) {
        padding: 0 5px;
      }
    }
  }
  @media only screen and (max-width: 850px) {
    width: 680px;
  }
  @media only screen and (max-width: 700px) {
    width: 480px;
  }
  @media only screen and (max-width: 500px) {
    width: 370px;
  }
  @media only screen and (max-width: 390px) {
    width: 270px;
  }
}
</style>
