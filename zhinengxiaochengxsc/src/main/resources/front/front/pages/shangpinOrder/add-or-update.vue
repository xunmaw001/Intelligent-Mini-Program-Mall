<template>
    <view class="content">
        <form class="app-update-pv">
                 <view
                         :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                         class="cu-form-group">
                     <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                           class="title">商品名称</view>
                     <input   disabled
                              :style='{"padding":"0 24rpx","boxShadow":"0px 6rpx 12rpx var(--publicSubColor)","margin":"6rpx 0rpx","borderColor":"#ccc","backgroundColor":"rgba(255, 255, 255, 1)","color":"#333","textAlign":"left","borderRadius":"40rpx 0","borderWidth":"0","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                              :disabled="ro.shangpinName" v-model="shangpin.shangpinName" placeholder="商品名称"></input>
                 </view>
                 <view
                         :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                         class="cu-form-group">
                     <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                           class="title">商品编号</view>
                     <input   disabled
                              :style='{"padding":"0 24rpx","boxShadow":"0px 6rpx 12rpx var(--publicSubColor)","margin":"6rpx 0rpx","borderColor":"#ccc","backgroundColor":"rgba(255, 255, 255, 1)","color":"#333","textAlign":"left","borderRadius":"40rpx 0","borderWidth":"0","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                              :disabled="ro.shangpinUuidNumber" v-model="shangpin.shangpinUuidNumber" placeholder="商品编号"></input>
                 </view>
                <view
                        :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(218, 220, 219, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"108rpx"}'
                        class="cu-form-group">
                    <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                          class="title">商品照片</view>
                    <view class="right-input" style="padding:0;textAlign:left">
                        <image
                                :style='{"width":"68rpx","boxShadow":"0 0 0px rgba(0,0,0,.3)","borderRadius":"100%","textAlign":"left","height":"68rpx"}'
                                class="avator" v-if="shangpin.shangpinPhoto" :src="baseUrl+shangpin.shangpinPhoto" mode="aspectFill">
                        </image>
                        <image
                                :style='{"width":"68rpx","boxShadow":"0 0 0px rgba(0,0,0,.3)","borderRadius":"100%","textAlign":"left","height":"68rpx"}'
                                class="avator" v-else src="../../static/gen/upload.png" mode="aspectFill"></image>
                    </view>
                </view>
							                <view
                        :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                        class="cu-form-group">
                    <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                          class="title">商品类型</view>
                    <input disabled
                           :style='{"padding":"0 24rpx","boxShadow":"0px 6rpx 12rpx var(--publicSubColor)","margin":"6rpx 0rpx","borderColor":"#ccc","backgroundColor":"rgba(255, 255, 255, 1)","color":"#333","textAlign":"left","borderRadius":"40rpx 0","borderWidth":"0","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                           :disabled="ro.shangpinValue"
                           v-model="shangpin.shangpinValue"
                           placeholder="商品类型"></input>
                </view>
                 <view
                         :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                         class="cu-form-group">
                     <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                           class="title">商品库存</view>
                     <input   disabled
                              :style='{"padding":"0 24rpx","boxShadow":"0px 6rpx 12rpx var(--publicSubColor)","margin":"6rpx 0rpx","borderColor":"#ccc","backgroundColor":"rgba(255, 255, 255, 1)","color":"#333","textAlign":"left","borderRadius":"40rpx 0","borderWidth":"0","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                              :disabled="ro.shangpinKucunNumber" v-model="shangpin.shangpinKucunNumber" placeholder="商品库存"></input>
                 </view>
            <view
                    :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                    class="cu-form-group">
                <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                      class="title">订单号</view>
                <input   disabled
                         :style='{"padding":"0 24rpx","boxShadow":"0px 6rpx 12rpx var(--publicSubColor)","margin":"6rpx 0rpx","borderColor":"#ccc","backgroundColor":"rgba(255, 255, 255, 1)","color":"#333","textAlign":"left","borderRadius":"40rpx 0","borderWidth":"0","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                         :disabled="ro.shangpinOrderUuidNumber" type="text" v-model="ruleForm.shangpinOrderUuidNumber" placeholder="订单号"></input>
            </view>
                <!-- 级联表的表id -->
                <input type="hidden" :value="shangpin.id" id="shangpinId" name="shangpinId"/>
                <view
                        :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                        class="cu-form-group">
                    <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                          class="title">购买数量</view>
                    <input   disabled
                             :style='{"padding":"0 24rpx","boxShadow":"0px 6rpx 12rpx var(--publicSubColor)","margin":"6rpx 0rpx","borderColor":"#ccc","backgroundColor":"rgba(255, 255, 255, 1)","color":"#333","textAlign":"left","borderRadius":"40rpx 0","borderWidth":"0","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                             :disabled="ro.buyNumber" type="number" v-model="ruleForm.buyNumber" placeholder="购买数量"></input>
                </view>
            <view
                    :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                    class="cu-form-group">
                <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                      class="title">快递公司</view>
                <input   disabled
                         :style='{"padding":"0 24rpx","boxShadow":"0px 6rpx 12rpx var(--publicSubColor)","margin":"6rpx 0rpx","borderColor":"#ccc","backgroundColor":"rgba(255, 255, 255, 1)","color":"#333","textAlign":"left","borderRadius":"40rpx 0","borderWidth":"0","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                         :disabled="ro.shangpinOrderCourierName" type="text" v-model="ruleForm.shangpinOrderCourierName" placeholder="快递公司"></input>
            </view>
            <view
                    :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                    class="cu-form-group">
                <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                      class="title">订单快递单号</view>
                <input   disabled
                         :style='{"padding":"0 24rpx","boxShadow":"0px 6rpx 12rpx var(--publicSubColor)","margin":"6rpx 0rpx","borderColor":"#ccc","backgroundColor":"rgba(255, 255, 255, 1)","color":"#333","textAlign":"left","borderRadius":"40rpx 0","borderWidth":"0","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                         :disabled="ro.shangpinOrderCourierNumber" type="text" v-model="ruleForm.shangpinOrderCourierNumber" placeholder="订单快递单号"></input>
            </view>
                <view :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                      class="cu-form-group">
                    <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                          class="title">订单类型</view>
                    <picker @change="shangpinOrderTypesChange" :value="shangpinOrderTypesIndex" :range="shangpinOrderTypesOptions" range-key="indexName">
                        <view
                                :style='{"padding":"0 24rpx","boxShadow":"0px 6rpx 12rpx var(--publicSubColor)","margin":"6rpx 0rpx","borderColor":"#ccc","backgroundColor":"rgba(255, 255, 255, 1)","color":"#333","textAlign":"left","borderRadius":"40rpx 0","borderWidth":"0","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                                class="uni-input">{{ruleForm.shangpinOrderTypes?ruleForm.shangpinOrderValue:"请选择订单类型"}}</view>
                    </picker>
                </view>

            <view class="btn">
                <button
                        :style='{"boxShadow":"0 0 16rpx rgba(0,0,0,0) inset","backgroundColor":"var(--publicMainColor)","borderColor":"#409EFF","borderRadius":"8rpx","color":"rgba(255, 255, 255, 1)","borderWidth":"0","width":"70%","fontSize":"32rpx","borderStyle":"solid","height":"80rpx"}'
                        @tap="onSubmitTap" class="bg-red">提交</button>
            </view>
        </form>

					<w-picker mode="dateTime" step="1" :current="false" :hasSecond="false" @confirm="insertTimeConfirm"
                              ref="insertTime" themeColor="#333333"></w-picker>
					<w-picker mode="dateTime" step="1" :current="false" :hasSecond="false" @confirm="createTimeConfirm"
                              ref="createTime" themeColor="#333333"></w-picker>


    </view>
</template>

<script>
    import wPicker from "@/components/w-picker/w-picker.vue";

    export default {
        data() {
            return {
                cross: '',
                ro:{
					shangpinOrderUuidNumber: true,
					addressId: false,
					shangpinId: false,
					yonghuId: false,
					buyNumber: true,
					shangpinOrderTruePrice: false,
					shangpinOrderCourierName: false,
					shangpinOrderCourierNumber: false,
					shangpinOrderTypes: false,
					shangpinOrderPaymentTypes: false,
					insertTime: false,
					createTime: false,
        },
            ruleForm: {
					shangpinOrderUuidNumber: this.getUUID(),//数字
					addressId: '',
					shangpinId: '',
					yonghuId: '',
					buyNumber: '',
					shangpinOrderTruePrice: '',
					shangpinOrderCourierName: '',
					shangpinOrderCourierNumber: '',
					shangpinOrderTypes: '',//数字
					shangpinOrderValue: '',//数字对应的值
					shangpinOrderPaymentTypes: '',//数字
					shangpinOrderPaymentValue: '',//数字对应的值
					insertTime: '',
					createTime: '',
            },
            // 登陆用户信息
            user: {},
				shangpinOrderTypesOptions: [],
							shangpinOrderTypesIndex : 0,
				shangpinOrderPaymentTypesOptions: [],
							shangpinOrderPaymentTypesIndex : 0,

        }
        },
        components: {
            wPicker
        },
        computed: {
            baseUrl() {
                return this.$base.url;
            },
        },
        async onLoad(options) {

		/*下拉框*/
			let shangpinOrderTypesParams = {
                page: 1,
                limit: 100,
                dicCode: 'shangpin_order_types',
            }
			let shangpinOrderTypes = await this.$api.page(`dictionary`, shangpinOrderTypesParams);
			this.shangpinOrderTypesOptions = shangpinOrderTypes.data.list
		/*下拉框*/
			let shangpinOrderPaymentTypesParams = {
                page: 1,
                limit: 100,
                dicCode: 'shangpin_order_payment_types',
            }
			let shangpinOrderPaymentTypes = await this.$api.page(`dictionary`, shangpinOrderPaymentTypesParams);
			this.shangpinOrderPaymentTypesOptions = shangpinOrderPaymentTypes.data.list


            // 如果是更新操作
            if (options.id) {
                this.ruleForm.id = options.id;
                // 获取信息
                let res = await this.$api.info(`shangpinOrder`, this.ruleForm.id);
                this.ruleForm = res.data;
            }
            if(options.shangpinOrderId){
                this.ruleForm.shangpinOrderId = options.shangpinOrderId;
            }
            // 跨表
            // this.styleChange()
        },
        methods: {
            // 下拉变化
            shangpinOrderTypesChange(e) {
                this.shangpinOrderTypesIndex = e.target.value
                this.ruleForm.shangpinOrderValue = this.shangpinOrderTypesOptions[this.shangpinOrderTypesIndex].indexName
                this.ruleForm.shangpinOrderTypes = this.shangpinOrderTypesOptions[this.shangpinOrderTypesIndex].codeIndex
            },
            shangpinOrderPaymentTypesChange(e) {
                this.shangpinOrderPaymentTypesIndex = e.target.value
                this.ruleForm.shangpinOrderPaymentValue = this.shangpinOrderPaymentTypesOptions[this.shangpinOrderPaymentTypesIndex].indexName
                this.ruleForm.shangpinOrderPaymentTypes = this.shangpinOrderPaymentTypesOptions[this.shangpinOrderPaymentTypesIndex].codeIndex
            },


            // styleChange() {
            // 	this.$nextTick(() => {
            // 		// document.querySelectorAll('.app-update-pv .cu-form-group .uni-yaoxianStyle-yaoxianStyle').forEach(el=>{
            // 		//   el.style.backgroundColor = this.addUpdateForm.yaoxianStyle.content.backgroundColor
            // 		// })
            // 	})
            // },


			// 日期控件
			insertTimeConfirm(val) {
                this.ruleForm.insertTime = val.result;
                this.$forceUpdate();
            },
			// 日期控件
			createTimeConfirm(val) {
                this.ruleForm.createTime = val.result;
                this.$forceUpdate();
            },




            getUUID() {
                return new Date().getTime();
            },
            async onSubmitTap() {
				if ((!this.ruleForm.shangpinOrderUuidNumber)) {
                    this.$utils.msg(`订单号不能为空`);
                    return
                }
				if ((!this.ruleForm.buyNumber) && (!this.$validate.isIntNumer(this.ruleForm.buyNumber)) && this.ruleForm.buyNumber >0) {
                    this.$utils.msg(`购买数量不能为空，不能小于0 格式为数字`);
                    return
                }
				if ((!this.ruleForm.shangpinOrderCourierName)) {
                    this.$utils.msg(`快递公司不能为空`);
                    return
                }
				if ((!this.ruleForm.shangpinOrderCourierNumber)) {
                    this.$utils.msg(`订单快递单号不能为空`);
                    return
                }
                if (this.ruleForm.id) {
                    await this.$api.update(`shangpinOrder`, this.ruleForm);
                } else {
                    await this.$api.save(`shangpinOrder`, this.ruleForm);
                }
                uni.setStorageSync('pingluenStateState', true);
                this.$utils.msgBack('提交成功');
            },
            getDate(type) {
                const date = new Date();
                let year = date.getFullYear();
                let month = date.getMonth() + 1;
                let day = date.getDate();
                if (type === 'start') {
                    year = year - 60;
                } else if (type === 'end') {
                    year = year + 2;
                }
                month = month > 9 ? month : '0' + month;;
                day = day > 9 ? day : '0' + day;
                return `${year}-${month}-${day}`;
            },
            toggleTab(str) {
                this.$refs[str].show();
            }
        }
    }
</script>
<style lang="scss" scoped>
    .container {
        padding: 20upx;
    }

    .content:after {
        position: fixed;
        top: 0;
        right: 0;
        left: 0;
        bottom: 0;
        content: '';
        background-attachment: fixed;
        background-size: cover;
        background-position: center;
    }

    textarea {
        border: 1upx solid #EEEEEE;
        border-radius: 20upx;
        padding: 20upx;
    }

    .title {
        width: 180upx;
    }

    .avator {
        width: 150upx;
        height: 60upx;
    }

    .right-input {
        flex: 1;
        text-align: left;
        padding: 0 24upx;
    }

    .cu-form-group.active {
        justify-content: space-between;
    }

    .cu-form-group .title {
        height: auto;
        line-height:30rpx
    }

    .btn {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-wrap: wrap;
        padding: 20upx 0;
    }

    .cu-form-group {
        padding: 0 24upx;
        background-color: transparent;
        min-height: inherit;
    }

    .cu-form-group+.cu-form-group {
        border: 0;
    }

    .cu-form-group uni-input {
        padding: 0 30upx;
    }

    .uni-input {
        padding: 0 30upx;
    }

    .cu-form-group uni-textarea {
        padding: 30upx;
        margin: 0;
    }

    .cu-form-group uni-picker::after {
        line-height: 80rpx;
    }

    .select .uni-input {
        line-height: 80rpx;
    }

    .input .right-input {
        line-height: 88rpx;
    }
</style>