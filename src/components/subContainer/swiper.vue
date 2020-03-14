<template>
  <div>
    <mt-swipe :auto="4000">
      <mt-swipe-item :class="{ full: isfull }"></mt-swipe-item>
      <mt-swipe-item></mt-swipe-item>
      <mt-swipe-item></mt-swipe-item>
    </mt-swipe>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {},
  props: ["isfull"]
};
</script>

<style lang="scss" scoped>
.mint-swipe {
  height: 250px;
  .mint-swipe-item {
    text-align: center;
  }
  .mint-swipe-item {
    &:nth-child(1) {
      background: url("../../images/animal1.jpg");
      height: 250px;
      width: 100%;
    }
    &:nth-child(2) {
      background: url("../../images/animal2.jpg");
      height: 250px;
      width: 100%;
    }
    &:nth-child(3) {
      background: url("../../images/animal3.jpg");
      height: 250px;
      width: 100%;
    }
  }
}
.mui-table-view {
  background-color: white;
  .mui-table-view-cell {
    border: 0;
  }
}
img {
  width: 60px;
  height: 60px;
}
.full{
  width: 100%;

}
</style>
