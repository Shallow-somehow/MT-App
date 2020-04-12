<template>

    <a href="#" class="recommend-item">
      <div class="card-wrapper">
        <div class="img-box">
          <img :src="meta.image" class="image" />
        </div>
        <div class="info-box">
          <div class="title">{{meta.title}}</div>
          <div class="score-line">
            <el-rate v-model="meta.score" disabled text-color="#ff9900" score-template="{value}"></el-rate>
            <span class="comment-number">{{meta.comNum}}个评价</span>
          </div>
          <div class="desc-line">
            <div class="desc">{{meta.address}}</div>
          </div>
          <div class="bottom-line">
            <div class="price-box">
              <span>
                <span class="yuan">￥</span>
                <span class="price-number">{{meta.price}}</span>
                <span class="price-desc">起</span>
              </span>
            </div>
          </div>
        </div>
      </div>
    </a>
</template>

<script>
export default {
  props: ["meta"]
};
</script>

<style >
</style>