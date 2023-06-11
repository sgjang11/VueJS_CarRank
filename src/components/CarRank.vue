<template >
    <div id="container">
        <h2>자동차 랭킹_장승기</h2>
        <p>인기가 많은 자동차 순위</p>
        <ul class="menu">
            <li v-for="(carRank,i) in carRanks" :key="i" :class="{active:i==crt}" @click="detail(i)">
                <div class="rank_wrap">
                    <span class="small">Ranking</span>
                    <span class="rank">{{i+1}}</span>
                </div>
                <div class="title">
                    {{carRank.title}}
                </div>
            </li>
        </ul>
        <div v-for="(carRank,i) in carRanks" :key="i">
            <div class="content" v-if="i==crt">
                <div class="img">
                    <img :src="carRank.img">
                </div>
                <ul class="content_list">
                    <li>가격 : {{carRank.price}}</li>
                    <li>종류 : {{carRank.fuel}}</li>
                    <li>배기량 : {{carRank.displacement}}</li>
                    <li>{{carRank.content}}</li>
                </ul>
            </div>
        </div>
    </div>
</template>
<script>
import carRank from '@/assets/carRank'
export default {
    data(){
        return {
            carRanks: carRank,
            crt:0
        }
    },
    methods: {
        detail(i){
            this.crt=i
        }
    }
}
</script>
<style >
    #container {
    text-align: center;
    padding: 20px;
    }

    p {
    font-size: 12px;
    padding-bottom: 20px;
    margin-bottom: 20px;
    border-bottom: 1px solid #ccc;
    }

    #container h2 {
    font-weight: 600;
    line-height: 2;
    }

    ul {
    list-style-type: none;
    }

    .menu {
    display: flex;
    margin-bottom: 20px;
    }

    .menu > li {
    width: 33%;
    display: flex;
    align-items: center;
    cursor: pointer;
    }

    .rank_wrap {
    width: 50px;
    background-color: aliceblue;
    margin-right: 10px;
    }

    .rank_wrap > span {
    display: block;
    }

    .rank {
    font-size: 30px;
    }

    .small {
    font-size: 12px;
    background-color: rgb(34, 109, 173);
    color: #ffff;
    }

    .title {
    background-color: #f7f7f7;
    width: calc(100% - 70px);
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    }

    .menu > li.active .small {
    background-color: black;
    }

    .menu > li.active .rank {
    color: #fff;
    background-color: black;
    }

    .menu > li.active .title {
    background-color: rgb(34, 109, 173);
    color: #fff;
    }

    .img img {
    width: 400px;
    }

    .content {
    display: flex;
    padding: 0 20px 0 0;
    }

    .content_list {
    text-align: left;
    margin-left: 20px;
    }

    .content_list li {
    border-bottom: 1px solid #eee;
    line-height: 2;
    }    
</style>