<template>
  <div class="shopping-container">
    <transition
      @before-enter="beforeEnter"
      @enter="Enter"
      @after-enter ="afterEnter"
    >
      <div class="ball" v-show="ballFlag" ref="ball"></div>
    </transition>
    <!-- 有了api过后轮播图需要通过父组件向子组件传递值 -->
    <div class="mui-card">
      <div class="mui-card-content">
        <div class="mui-card-content-inner">
          <swiper :isfull="false"></swiper>
        </div>
      </div>
    </div>

    <div class="mui-card">
      <div class="mui-card-header">Tony熊</div>
      <div class="mui-card-content">
        <div class="mui-card-content-inner">
          <p class="price">
            <span><del>市场价:1999</del></span>
            <span>活动价: 1499</span>
          </p>
          <p>购买数量:<numbox @getcount="getSelectedCount"></numbox></p>
          <mt-button type="danger" size="small">立即购买</mt-button>
          <mt-button type="primary" size="small" @click="addToShopCar">加入购物车</mt-button>
        </div>
      </div>
    </div>
    <div class="mui-card">
      <div class="mui-card-header">商品参数</div>
      <div class="mui-card-content">
        <div class="mui-card-content-inner">
          <p>商品货号：</p>
          <p>库存情况：件</p>
          <p>上架时间：</p>
        </div>
      </div>
      <div class="mui-card-footer">
        <mt-button type="primary" size="large" plain @click="goodsdesc"
          >图文介绍</mt-button
        >
        <mt-button type="danger" size="large" plain @click="goodscomment"
          >商品评论</mt-button
        >
      </div>
    </div>
  </div>
</template>

<script>
import swiper from "../subContainer/swiper.vue";
import numbox from "../subContainer/goodsinfo_numbox.vue";
export default {
  data() {
    return {
      id: 1,
      selectedCount: 1,
      ballFlag: false,
      goodsinfo: {},
    };
  },
  methods: {
    getSelectedCount(count) {
      this.selectedCount = count;
      console.log("父组件拿到的数量值为： " + this.selectedCount);
    },
    goodsdesc(id) {
      this.$router.push({ name: "desc", params: { id } });
    },
    goodscomment(id) {
      this.$router.push({ name: "comment", params: { id } });
    },
    addToShopCar() {
      this.ballFlag = !this.ballFlag;
      var goodsinfo = {
        id: this.id,
        count: this.selectCount,
        price: null,
        selected: true
      };
    },

    beforeEnter(el) {
      el.style.transform = "translate(0, 0)";
    },
    Enter(el, done) {
      el.offsetWidth;
      // 获取小球的 在页面中的位置
      const ballPosition = this.$refs.ball.getBoundingClientRect();
      // 获取 徽标 在页面中的位置
      const badgePosition = document
        .getElementById("badge")
        .getBoundingClientRect();
      const xDist = badgePosition.left - ballPosition.left;
      const yDist = badgePosition.top - ballPosition.top;
      el.style.transform = `translate(${xDist}px, ${yDist}px)`;
      el.style.transition = "all 0.5s cubic-bezier(.4,-0.3,1,.68)";
      done();
    },
    afterEnter(el) {
      this.ballFlag = !this.ballFlag;
    }
  },
  components: {
    swiper,
    numbox
  }
};
</script>

<style lang="scss" scoped>
.shopping-container {
  background: #eee;
  overflow: hidden;
  .ball {
    width: 15px;
    height: 15px;
    border-radius: 50%;
    background-color: red;
    position: absolute;
    z-index: 99;
    top: 483px;
    left: 146px;
  }
  .mui-card-footer{
    display: block;
    button{
      margin: 15px 0;
    }
  }
}
</style>
