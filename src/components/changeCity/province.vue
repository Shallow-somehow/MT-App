<template>
  <div>
    <span>按省份选择</span>
    <m-select
      :list="provinceList"
      title="省份"
      :value="province"
      :showWrapperActive="provinceActive"
      @change_active="changeProvinceActive"
      @change="changeProvince"
      area="province"
    ></m-select>
    <m-select
      :list="cityList"
      title="城市"
      :value="city"
      :showWrapperActive="cityActive"
      @change_active="changeCityActive"
      @change="changeCity"
      :disabled="cityDisabled"
      area="city"
    ></m-select>
    <span>
      直接搜索:
      <el-select
        v-model="searchWord"
        filterable
        remote
        reserve-keyword
        placeholder="请输入关键词"
        :remote-method="remoteMethod"
        :loading="loading"
      >
        <el-option v-for="item in searchList" :key="item.value" :label="item" :value="item"></el-option>
      </el-select>
    </span>
  </div>
</template>

<script>
import MSelect from "./select";
import api from "@/api/index.js";
export default {
  created() {
    api.getProvinceList().then(res => {
      // console.log(res);
      this.provinceList = res.data.data.map(item => {
        item.name = item.provinceName;
        return item;
      });
    });
  },
  data() {
    return {
      cityDisabled: true,
      provinceList: [],
      province: "省份",
      cityList: [],
      city: "城市",
      cityActive: false,
      provinceActive: false,
      searchList: [
        "青岛",
        "淄博",
        "济南",
        "烟台",
        "枣庄",
        "东营",
        "潍坊",
        "济D宁",
        "泰安",
        "威海",
        "日照",
        "莱芜"
      ],
      searchWord: "",
      loading: false
    };
  },
  components: {
    MSelect
  },
  methods: {
    changeProvinceActive(flag) {
      this.provinceActive = flag;
      if (flag) {
        this.cityActive = false;
      }
    },
    changeCityActive(flag) {
      this.cityActive = flag;
      if (flag) {
        this.provinceActive = false;
      }
    },
    changeProvince(item) {
      this.province = item.name;
      this.cityDisabled = false;
      this.cityList = item.cityInfoList;
    },
    changeCity(item) {
      this.city = item.name;
      this.$store.dispatch('setPosition', item)
      this.$router.push({name: 'index'})
    },
    remoteMethod(e) {
      //  请求后端接口
    }
  }
};
</script>

<style lang="scss">
@import "@/assets/css/changecity/iselect.scss";
</style>