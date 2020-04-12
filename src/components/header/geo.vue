<template>
    <div class="m-geo">
        <div class="position">
            <i class="el-icon-location"/>
            {{$store.state.position.name}}
            <router-link class="changeCity" :to="{name:'changeCity'}">
                切换城市
            </router-link>
            [
            <a class='minInfo' href="#" v-for="(item, index) in nearCity"
                :key="index"
            >{{item.name}}</a>

            ] 
        </div>
        <div class="m-user" v-if="!$store.state.userName">
            <router-link :to="{name:'login'}" class="login">
                立即登录
            </router-link>
             <router-link :to="{name:'register'}" class="register">
               注册
            </router-link>
        </div>
    </div>
</template>

<script>
import api from '@/api/index.js'
export default {
    data() {
        return {
            nearCity: []
        }
    },
    created () {
        api.getCurPosition().then(res => {
            console.log(res)
            this.$store.dispatch('setPosition', res.data.data)
            this.nearCity = res.data.data.nearCity;
        })
    },
    watch: {
        "$store.state.position" : function () {
            this.nearCity = this.$store.state.position.nearCity
        }
    }
}
</script>