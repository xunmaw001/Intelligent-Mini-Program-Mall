<template>
    <view>
        <view class="cu-chat">
            <view v-for="(item,index) in list" v-bind:key="index">
                <view v-if="item.chatIssue" class="cu-item self">
                    <view class="main">
                        <view class="content bg-green shadow">
                            <text>{{item.chatIssue}}</text>
                        </view>
                    </view>
                    <view class="cu-avatar radius" style="background-image:url(https://ossweb-img.qq.com/images/lol/web201310/skin/big107000.jpg);"></view>
                    <view class="date">{{item.insertTime}}</view>
                </view>
                <view v-if="item.chatReply" class="cu-item">
                    <view class="cu-avatar radius" style="background-image:url(https://ossweb-img.qq.com/images/lol/web201310/skin/big143004.jpg);"></view>
                    <view class="main">
                        <view class="content shadow">
                            <text>{{item.chatReply}}</text>
                        </view>
                    </view>
                    <view class="date ">{{item.updateTime}}</view>
                </view>
            </view>
        </view>

        <view class="cu-bar foot input">
            <input v-model="chatIssue" class="solid-bottom" :adjust-position="false" :focus="false" maxlength="300" cursor-spacing="10"></input>
            <button @tap="onSendTap" class="cu-btn bg-green shadow">发送</button>
        </view>

    </view>
</template>

<script>
    export default {
        data() {
            return {
                // 定时器
                inter: {},
                list: [],
                chatIssue: ''
            };
        },
        onLoad() {
            let _this = this;
            let inter = setInterval(function() {
                _this.init();
            }, 3000)
            this.inter = inter
        },
        onUnload() {
            if (this.inter) {
                // 清除定时器
                clearInterval(this.inter);
            }
        },
        methods: {
            async onSendTap() {
                await this.$api.save('chat', {
                    chatIssue: this.chatIssue,
                    zhuangtaiTypes: 1,
                    chatTypes: 1,
                    issueTime:this.$utils.getCurDateTime(),
                });
                this.chatIssue = '';
                this.init();
            },
            async init() {
                let res = await this.$api.page('chat', {
                    page: 1,
                    limit: 999,
                });
                this.list = res.data.list;
            }
        }
    }
</script>

<style>
    page {
        padding-bottom: 100upx;
    }
</style>
