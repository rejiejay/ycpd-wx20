<!-- 
  - 我的券列表 
  -->
<template>
  <div class="ticket-list">
    <!-- 头部导航栏 -->
    <mt-header title="我的优惠券">
        <router-link to="/user/index" slot="left">
            <mt-button icon="back"></mt-button>
        </router-link>
    </mt-header>

    <!-- 顶部选项卡 -->
    <mt-navbar v-model="navbarSelected">
        <mt-tab-item id="unused">未使用</mt-tab-item>
        <mt-tab-item id="used">已使用</mt-tab-item>
        <mt-tab-item id="expired">已过期</mt-tab-item>
    </mt-navbar>

    <!-- 显示面板 -->
    <mt-tab-container v-model="navbarSelected">

      <!-- 未使用 -->
      <mt-tab-container-item id="unused">
        <div class="ticket-list">
            <div class="ticket-item">
                <div class="ticket-item-content">
                    <div class="ticket-item-left">
                        <div class="item-left-title flex-start">
                            <div class="item-left-main flex-rest">
                                上门保养
                            </div>
                            <div class="item-left-sub">
                                详情 >
                            </div>
                        </div>
                        <div class="item-left-details">
                            <div>粵B3H97T</div>
                            <div>在线预约，技师上门，足不出户，享受VIP服务</div>
                        </div>
                        <div class="item-left-bottom">核销码: 201710171YZVNlgYV</div>
                    </div>
                    <div class="ticket-item-right" @click="qrCodeVisible = true;">
                        <div class="item-right-content">
                            <div class="item-right-code">核销码</div>
                            <div class="item-right-time">2018-6-26前有效</div>
                        </div>
                    </div>
                    <div class="ticket-item-background">
                        <img src="https://ycpduser.oss-cn-shenzhen.aliyuncs.com/wx20/user/ticket/arrive_bg.png" />
                    </div>
                </div>
            </div>
        </div>
      </mt-tab-container-item>

      <!-- 已使用 -->
      <mt-tab-container-item id="used">
        <div class="ticket-none">暂无券</div>
      </mt-tab-container-item>

      <!-- 已过期 -->
      <mt-tab-container-item id="expired">
        <div class="ticket-none">暂无券</div>
      </mt-tab-container-item>
    
    </mt-tab-container>

    <!-- 显示二维码 -->
    <el-dialog
        title="出示店员核销"
        :modal="true"
        :fullscreen="true"
        :visible.sync="qrCodeVisible"
    >
        <div class="dialog-qrcode">
            <img src="http://p6ygud9kn.bkt.clouddn.com/YCPD/wx20/qrcode.png" />

            <div class="close-qrcode" @click="qrCodeVisible = false;">确认</div>
        </div>
    </el-dialog>
  </div>
</template>

<script>

import ajaxs from './ajaxs';

// mint-ui 框架
import Vue from 'vue';
import { Header, Button, Navbar, TabItem, TabContainer, TabContainerItem } from 'mint-ui';

Vue.component('mt-header', Header);
Vue.component('mt-button', Button);
Vue.component('mt-navbar', Navbar);
Vue.component('mt-tab-item', TabItem);
Vue.component('mt-tab-container', TabContainer);
Vue.component('mt-tab-container-item', TabContainerItem);

// element-ui
import { Dialog } from 'element-ui';
Vue.use(Dialog);

export default {
    name: 'myTicketList',

    data () {
        return {
            // 顶部选项卡
            navbarSelected: "unused", // 未使用:unused 已使用:used 已过期:expired
            qrCodeVisible: false,
        }
    },

    mounted() {
    },

    methods: {
    }
}

</script>

<style scoped lang="less">
@black1: #303133;
@black2: #606266;
@black3: #909399;
@black4: #C0C4CC;


// 初始化样式
.ticket-list {
    width: 100%;
    min-height: 100%;
    background: #efefef;
    overflow: hidden;
}

// 头部导航栏
.ticket-list .mint-header {
    background: #d00;
    margin-bottom: 15px;
}

// 顶部选项卡
.ticket-list .mint-navbar {
    position: relative;
    z-index: 2;

    .mint-tab-item-label {
        font-size: 16px;
    }

    .is-selected {
        border-bottom: 3px solid #F56C6C;
        color: #F56C6C;
        text-decoration: none;
    }
}

// 显示面板
.ticket-list .mint-tab-container {
  position: relative;
  top: 1px;

  .ticket-list {
    background: #fff;
    padding-top: 15px;

    .ticket-item {
        padding: 0px 15px 15px 15px;

        .ticket-item-content {
            position: relative;
        }

        .ticket-item-left {
            position: absolute;
            top: 0px;
            left: 0px;
            width: 69%;
            height: 100%;
            z-index: 1;

            .item-left-title {
                padding: 10px 10px 10px 15px;
                color: #fff;
                font-size: 14px;

                .item-left-sub {
                    font-size: 12px;
                    color: @black1;
                }
            }

            .item-left-details {
                font-size: 12px;
                line-height: 16px;
                padding: 0px 10px 0px 15px;
                color: @black1;
            }

            .item-left-bottom {
                position: absolute;
                padding: 10px 10px 10px 15px;
                bottom: 0px;
                left: 0px;
                font-size: 12px;
                color: #fff;
            }
        }

        .ticket-item-right {
            position: absolute;
            top: 0px;
            right: 0px;
            width: 31%;
            height: 100%;
            text-align: center;
            font-size: 12px;
            z-index: 1;

            .item-right-content {
                position: absolute;
                top: 55%;
                width: 100%;
                color: @black1;
            }
        }

        .ticket-item-background {
            width: 100%;
            height: 100%;

            img {
                display: block;
                width: 100%;
                height: 100%;
            }
        }
    }
  }

  .ticket-none {
    padding: 15px;
    text-align: center;
    font-size: 14px;
    color: #606266;
  }
}

// 二维码核销
.ticket-list .el-dialog {
  .dialog-qrcode {
    img {
      display: block;
      padding-bottom: 15px;
      width: 100%;
      height: 100%;
    }

    .close-qrcode {
      position: relative;
      display: block;
      color: #FFFFFF;
      background-color: #1AAD19;
      padding-left: 14px;
      padding-right: 14px;
      box-sizing: border-box;
      font-size: 18px;
      text-align: center;
      text-decoration: none;
      color: #FFFFFF;
      line-height: 2.55555556;
      border-radius: 5px;
      -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
      overflow: hidden;
    }
  }
}

</style>
