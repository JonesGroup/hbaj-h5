<!--
 * @Author: yangyuan
 * @Date: 2020-04-19 18:58:48
 * @Email: 1367511704@qq.com
 * @LastEditTime: 2020-05-18 22:12:37
 * @Description: 
 -->
<template>
    <div class="page-view">
        <Header title="我的通知" :isBack="true" v-if="isMiniprogram"></Header>
        <div class="scroll-view-wrapper">
            <div class="message-content">
                <List></List>
            </div>
        </div>
        <Footer></Footer>
    </div>
</template>

<script>
import List from "./list";
import Header from "@/components/common/header";
import Footer from "@/components/common/footer";
import utils from "@/widget/utils";
export default {
    data() {
        return {
            menupB: true,
            isMiniprogram: utils.isMiniprogram()
        };
    },
    components: {
        List,
        Header,
        Footer
    }
};
</script>
<style lang="less">
.message-content {
    height: 100%;
    background: #fff;
}
</style>
