<!--
 * @Author: yangyuan
 * @Date: 2020-04-16 21:03:29
 * @Email: 1367511704@qq.com
 * @LastEditTime: 2020-05-28 17:37:11
 * @Description: 
 -->
<template>
    <div class="news-content-item" @click="toNewsDetail(item.id)">
        <div class="news-item-detail">
            <div class="news-item-title">
                <div class="text">
                    <p class="ellipsisLineTwo">{{ item.title }}</p>
                </div>
            </div>
            <div class="news-item-digest">
                <p class="ellipsis">
                    {{ item.summary }}
                </p>
            </div>
            <div class="news-item-source">
                <div class="organization">
                    <!-- <span>发布机构:</span> -->
                    <span>{{ item.author }}</span>
                </div>
                <div class="publishTime">
                    <!-- <span>发布时间:</span> -->
                    <span>{{ item.publishTime | formaData }}</span>
                </div>
            </div>
        </div>
        <div class="news-item-thumb ui-lazyLoad-pic" v-lazy :data-src="globalConfig.imagePath + item.imageUrl">
            <!-- <img :src="globalConfig.imagePath + item.imageUrl" :alt="item.title"> -->
        </div>
    </div>
</template>

<script>
import store from "@/widget/store";
import "@/widget/lazyLoad";
export default {
    data() {
        return {
            newsDefaultImage: store.get("newsDefaultImage", "local")
        };
    },
    props: {
        item: {
            type: Object,
            default: {}
        }
    },
    methods: {
        toNewsDetail(id) {
            this.$router.push({
                name: "newsDetail",
                params: {
                    id
                }
            });
        }
    }
};
</script>

<style lang="less">
.news-content-item {
    display: flex;
    padding-top: 0.38rem;
    padding-bottom: 0.4rem;
    padding-right: 0.2rem;
    padding-left: 0.2rem;
    border-bottom: 0.02rem solid rgba(221, 221, 221, 1);
    background: #fff;
    &:last-child {
        border-bottom: none;
    }
    .news-item-detail {
        flex: 1;
        width: 4.44rem;
        .news-item-title {
            width: 100%;
            .text {
                height: 0.8rem;
                p {
                    font-size: 0.28rem;
                    font-family: MicrosoftYaHei;
                    color: rgba(51, 51, 51, 1);
                    line-height: 0.4rem;
                    letter-spacing: 0.01rem;
                    -webkit-background-clip: text;
                }
            }
        }
        .news-item-digest {
            width: 100%;
            margin-top: 0.14rem;
            margin-bottom: 0.15rem;
            p {
                font-size: 0.24rem;
                font-family: MicrosoftYaHei;
                color: rgba(102, 102, 102, 1);
                line-height: 0.31rem;
                -webkit-background-clip: text;
            }
        }
        .news-item-source {
            display: flex;
            align-content: center;
            justify-content: space-between;
            width: 100%;
            span {
                font-size: 0.19rem;
                font-family: MicrosoftYaHei;
                color: rgba(153, 153, 153, 1);
                line-height: 0.26rem;
                -webkit-background-clip: text;
                word-break: break-all;
            }
        }
    }
    .news-item-thumb {
        width: 2.44rem;
        height: 1.64rem;
        margin-left: 0.22rem;
        // background: #f0f0f0;
        img {
            width: 100%;
            height: 100%;
        }
    }
}
</style>
