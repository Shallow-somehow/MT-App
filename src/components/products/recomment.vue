<template>
  <div class="m-reight-content">
    <img class="mini-map" src="../../assets/img/map.png" alt="地图" />
    <div class="right-box">
      <div class="top-nav-box">
        <div class="label">猜你喜欢</div>
      </div>
      <div class="recommend-list">
        <right-box v-for="(item, index) in recommend_list" :key="index" :meta="item" />
      </div>
    </div>
  </div>
</template>

<script>
import RightBox from "./rightBox";
export default {
  data() {
    return {
      recommend_list: [
        {
          image:
            "//p1.meituan.net/msmerchant/0848bee67ec568c91ef2a4f9bdf590f9168886.jpg@190w_106h_1e_1c",
          title: "丫咪饭团",
          score: 5.0,
          address: "盛隆街",
          price: 6.9,
          comNum: 848
        },
        {
          image:
            "//p1.meituan.net/msmerchant/0b0b24d19569c515e71f5a487509afab75729.jpg@190w_106h_1e_1c",
          title: "味蜀吾老火锅（莱阳店）",
          score: 5.0,
          address: "盛隆街",
          price: 58.0,
          comNum: 1750
        },
        {
          image:
            "//p0.meituan.net/mogu/b49beca0b2e1e94c1a9a504c4906385f285244.jpg@190w_106h_1e_1c",
          title: "高老庄饺子自助",
          score: 5.0,
          address: "盛隆街",
          price: 27.5,
          comNum: 1163
        },
        {
          image:
            "//p0.meituan.net/deal/2b81140673e1a6d79ca662604c235aa131127.jpg@190w_106h_1e_1c",
          title: "密秀精灵",
          score: 4.0,
          address: "中心客运站",
          price: 2.48,
          comNum: 204
        },
        {
          image:
            "//p0.meituan.net/msmerchant/08bac43bdb9b3a6feecb7b2e628924ed197799.jpg@190w_106h_1e_1c",
          title: "麦香园蛋糕",
          score: 5.0,
          address: "",
          price: 7.9,
          comNum: 1019
        }
      ]
    };
  },
  components: {
    RightBox
  }
};
</script>
