<template>
  <div>
    <nav-header></nav-header>
    <nav-bread>
      <span>Goods</span>
    </nav-bread>
    <div class="accessory-result-page accessory-page">
      <div class="container">
        <div class="filter-nav">
          <span class="sortby">Sort by:</span>
          <a href="javascript:void(0)" class="default cur">Default</a>
          <a href="javascript:void(0)" class="price">Price <svg class="icon icon-arrow-short"><use xlink:href="#icon-arrow-short"></use></svg></a>
          <a href="javascript:void(0)" class="filterby stopPop" @click="showFilterPop">Filter by</a>
        </div>
        <div class="accessory-result">
          <!-- filter -->
          <div class="filter stopPop" id="filter" :class="{'filterby-show':filterBy}">
            <dl class="filter-price">
              <dt>Price:</dt>
              <dd><a href="javascript:void(0)" :class="{'cur':priceChecked=='all'}" @click="priceChecked='all'">All</a></dd>
              <!-- 利用循环项的index，给被点击的价格区间加上cur类名，表示该区间当前处于被选定状态 -->
              <dd v-for="(price, index) of priceFilter">
                <a href="javascript:void(0)"  @click="setPriceFilter(index)" :class="{'cur':priceChecked==index}">{{price.startPrice}}-{{price.endPrice}}</a>
              </dd>
            </dl>
          </div>

          <!-- search result accessories list -->
          <div class="accessory-list-wrap">
            <div class="accessory-list col-4">
              <ul>
                <li v-for="(item, index) of goodsList">
                  <div class="pic">
                    <a href="#"><img :src="'/static/'+item.productImg" alt=""></a>
                  </div>
                  <div class="main">
                    <div class="name">{{item.productName}}</div>
                    <div class="price">{{item.productPrice}}</div>
                    <div class="btn-area">
                      <a href="javascript:;" class="btn btn--m">加入购物车</a>
                    </div>
                  </div>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- 遮罩 -->
    <!-- 遮罩效果：手机端点击fiterby，显示出价格筛选菜单时，同时弹出遮罩 -->
    <div class="md-overlay" v-show="overLayFlag" @click="closePop"></div>
    <nav-footer></nav-footer>
  </div>
</template>

<script>
import '@/assets/css/base.css'
import '@/assets/css/product.css'

import navHeader from './components/navHeader'
import navFooter from './components/navFooter'
import navBread from './components/navBread'
import axios from 'axios'

export default {
  name: 'GoodsList',
  data () {
    return {
      goodsList: [],
      priceFilter: [{
        "startPrice": 0,
        "endPrice": 500
      }, {
        "startPrice": 500,
        "endPrice": 1000
      }, {
        "startPrice": 1000,
        "endPrice": 2000
      }],
      priceChecked: 'all',
      filterBy: false,
      overLayFlag: false
    }
  },
  components: {
    navHeader,
    navFooter,
    navBread
  },
  mounted: function () {
    this.getGoodsList();
  },
  methods: {
    getGoodsList () {
      axios.get("/goods").then((result)=>{
        var res = result.data;
        // 返回的result是一个数组，将它放到goodsList中准备进行遍历
        this.goodsList = res.result;
      })
    },
    // 手机端点击filterby时，弹出价格区间选择，并且显示遮罩
    showFilterPop () {
      this.filterBy = true;
      this.overLayFlag = true;
    },
    // 首先，将被点击的价格区间的index赋值给priceChecked,实现价格区间的选定。
    // 然后，调用closepop方法关闭弹出的价格区间筛选菜单以及遮罩
    setPriceFilter (index) {
      this.priceChecked = index;
      this.closePop();
    },
    // 手机端点击遮罩时，关闭价格区间选择，并且隐藏遮罩
    closePop () {
      this.filterBy = false;
      this.overLayFlag = false;
    }
  }
}
</script>
