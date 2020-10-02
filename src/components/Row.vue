<template>
    <div class="Row">
        <div class="title">
            {{chart.title}}
        </div>
        <Bar :ranges="chart.ranges" :forecast="chart.forecast"/>
        <div class="tooltip">
            <Number :min="chart.minValue" :max="chart.maxValue"/>
        </div>
    </div>
</template>

<script>
import Bar from '@/components/Bar.vue';
import Number from '@/components/Number.vue';

export default {
  name: 'Row',
  components: {
    Bar,
    Number,
  },
  props: ['chart'],
};

</script>

<style scoped>
.title {
  min-height: 45px;
  display: flex;
  align-items: center;
  font-size: 12px;
}
</style>
