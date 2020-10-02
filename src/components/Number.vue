<template>
  <div class="tip">
    <div class="minValue">{{min}}</div>
    <div class="maxValue">{{max}}</div>
  </div>
</template>

<script>
export default {
  name: 'Tip',
  props: ['min', 'max'],
};
</script>

<style scoped>
.tip {
  min-height: 30px;
  padding: 0 19px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 10px;
  color: #cdcdcd;
}
</style>
