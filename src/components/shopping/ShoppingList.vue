<template>
  <div class="shopping-list">
    <div class="goods-item" @click="getinfo(id)">
      <img
        src="http://img.alicdn.com/bao/uploaded/i1/2647305308/O1CN01ksIepT1p56tpx7Cju_!!0-item_pic.jpg_220x220.jpg"
        alt=""
      />
       <div class="shopping-info">
        <p class="price">
          <span class="new">¥69.00</span>
          <span class="old">¥89.00</span>
        </p>
        <p class="title">网红男小脚裤</p>
        <p class="sell">
          <span>月销: 100件</span>
          <span>剩余: 1件</span>
        </p>
      </div>
    </div>
    <div class="goods-item">
      <img
        src="http://img.alicdn.com/bao/uploaded/i1/2647305308/O1CN01ksIepT1p56tpx7Cju_!!0-item_pic.jpg_220x220.jpg"
        alt=""
      />
       <div class="shopping-info">
        <p class="price">
          <span class="new">¥69.00</span>
          <span class="old">¥89.00</span>
        </p>
        <p class="title">网红男小脚裤</p>
        <p class="sell">
          <span>月销: 100件</span>
          <span>剩余: 1件</span>
        </p>
      </div>
    </div>
    <div class="goods-item">
      <img
        src="http://img.alicdn.com/bao/uploaded/i1/2647305308/O1CN01ksIepT1p56tpx7Cju_!!0-item_pic.jpg_220x220.jpg"
        alt=""
      />
      <div class="shopping-info">
        <p class="price">
          <span class="new">¥69.00</span>
          <span class="old">¥89.00</span>
        </p>
        <p class="title">网红男小脚裤</p>
        <p class="sell">
          <span>月销: 100件</span>
          <span>剩余: 1件</span>
        </p>
      </div>
      
    </div>
    <mt-button type="danger" size="large">加载更多</mt-button>
  </div>
</template>

<script>
export default {
  data(){
    return {
      id : 200
    }
  },
  created(){

  },
  methods:{
    getinfo(id){
      console.log("hehe") 
      // this.$router.push("/HomeContainer/shoppinginfo/"+ id)  //方式一
      this.$router.push({ name :"goodsinfo", params:{id}})
    }
  }
};
</script>
// 
<style lang="scss">
.shopping-list {
  display: flex;
  padding: 6px;
  justify-content: space-between;
  // 放不下就换行的样式
  flex-wrap: wrap;
  .goods-item {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-height: 266px; 
    margin: 4px 0;
    width: 49%;
    border: 1px solid #ccc;
    box-shadow: 0 0 8px rgb(233, 225, 225);
    .shopping-info{
      background-color: #eee;
      p{
        margin: 0px;
        padding: 4px;
        .new{
          color: red;
          font-weight:bold;
          font-size: 16px;
        }
        .old{
          text-decoration: line-through;
          font-size: 12px;
          margin-left: 10px;
        }
     
      
      
      }
      
    }
    img {
      width: 100%;
    }
    .title {
      font-size: 14px;
      font-weight: bold;
      color: black;
    }
    
  }
}
 .sell{
    display: flex;
    justify-content: space-between;
    font-size: 13px;
  }
</style>
