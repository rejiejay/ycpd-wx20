<!-- 
  - 个人中心页面 
  -->
<template>
  <div class="user">
    <!-- 头部 -->
    <div class="user-header">
      <div class="user-header-main">

        <!-- 耳机 -->
        <div class="headphones-content">
          <span v-on:click="callService">
            <headphones color="#fff" width="24" height="24"/>
          </span>
        </div>

        <!-- 已登录 头像 -->
        <div 
          v-if="loginIofor"
          v-on:click="$router.push('/user/infor')"
          class="header-login main-flex-start"
        >
          <div class="login-portrait" v-if="loginIofor.headImageUrl">
            <img alt="用户头像" :src="loginIofor.headImageUrl" />
          </div>
          <div class="login-portrait" v-else>
            <svg class="personnel" width="42" height="42" t="1526456513719" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="20331" xmlns:xlink="http://www.w3.org/1999/xlink" >
              <path fill="#d8d8d8" d="M512.0181274414062 140.7236328125c-125.93957519531247 0-228.48156738281247 102.50326538085938-228.48156738281247 228.48074340820312 0 125.90167236328126 102.46701049804688 228.44448852539062 228.48156738281247 228.44448852539062 125.97665405273438 0 228.517822265625-102.54199218749999 228.517822265625-228.44448852539062 0-125.97747802734375-102.54116821289061-228.48074340820312-228.517822265625-228.48074340820312z" p-id="20332"></path>
              <path fill="#d8d8d8" d="M688.11962890625 592.4355773925781c-48.68206787109375 38.48208618164063-109.30682373046875 62.32461547851563-176.10150146484375 62.32461547851563-66.79550170898438 0-127.38153076171872-23.915863037109375-176.17565917968753-62.32461547851563C243.4666748046875 651.2484130859374 179.14804077148432 754.5303344726562 170.31338500976562 874.1483764648438c32.343475341796875 4.396728515625001 89.89892578124999 9.127990722656248 172.03436279296875 9.127990722656248h339.1916198730469c82.17333984375 0 139.7650451660156-4.731262207031249 172.14724731445312-9.127990722656248-8.762145996093748-119.69384765625-73.07995605468749-222.89996337890622-165.5669860839844-281.71279907226557z" p-id="20333"></path>
            </svg>
          </div>
          <div class="login-content">
            <div>{{loginIofor.ContactName}}</div>
            <div>{{loginIofor.Mobile}}</div>
          </div>
          <div class="login-icon">
            <icon
              color="#fff"
              width="12"
              height="26"
              name="angle-right"
            />
          </div>
        </div>
        <!-- 未登录 头像 -->
        <div 
          v-else 
          v-on:click="jumpToLogin()"
          class="header-login main-flex-start"
        >
          <div class="login-portrait">
            <svg class="personnel" width="42" height="42" t="1526456513719" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="20331" xmlns:xlink="http://www.w3.org/1999/xlink" >
              <path fill="#d8d8d8" d="M512.0181274414062 140.7236328125c-125.93957519531247 0-228.48156738281247 102.50326538085938-228.48156738281247 228.48074340820312 0 125.90167236328126 102.46701049804688 228.44448852539062 228.48156738281247 228.44448852539062 125.97665405273438 0 228.517822265625-102.54199218749999 228.517822265625-228.44448852539062 0-125.97747802734375-102.54116821289061-228.48074340820312-228.517822265625-228.48074340820312z" p-id="20332"></path>
              <path fill="#d8d8d8" d="M688.11962890625 592.4355773925781c-48.68206787109375 38.48208618164063-109.30682373046875 62.32461547851563-176.10150146484375 62.32461547851563-66.79550170898438 0-127.38153076171872-23.915863037109375-176.17565917968753-62.32461547851563C243.4666748046875 651.2484130859374 179.14804077148432 754.5303344726562 170.31338500976562 874.1483764648438c32.343475341796875 4.396728515625001 89.89892578124999 9.127990722656248 172.03436279296875 9.127990722656248h339.1916198730469c82.17333984375 0 139.7650451660156-4.731262207031249 172.14724731445312-9.127990722656248-8.762145996093748-119.69384765625-73.07995605468749-222.89996337890622-165.5669860839844-281.71279907226557z" p-id="20333"></path>
            </svg>
          </div>
          <div class="login-content">
            注册会员
          </div>
          <div class="login-icon">
            <icon
              color="#fff"
              width="12"
              height="26"
              name="angle-right"
            />
          </div>
        </div>

        <!-- 项目 按钮 已登录 -->
        <div v-if="loginIofor" class="header-tab main-flex-start">
          <div class="header-tab-item">
            <div class="item-name">{{userRelated.points}}</div>
            <div class="item-name">积分</div>
            <div class="header-tab-interval"></div>
          </div>
          <div 
            class="header-tab-item"
            v-on:click="jumpToUrl(`http://${locationhost}/wx/Coupons.aspx`)"
          >
            <div class="item-name">{{loginIofor.Coupons}}</div>
            <div class="item-name">优惠券</div>
            <div class="header-tab-interval"></div>
          </div>
          <div class="header-tab-item">
            <div class="item-name">VIP-{{userRelated.VIP.grade}}</div>
            <div class="item-name">{{userRelated.VIP.name}}</div>
          </div>
        </div>
        <!-- 项目 按钮 未登录 -->
        <div v-else class="header-tab main-flex-start">
          <div class="header-tab-item">
            <integration width="24" height="24" color="#fff"/>
            <div class="item-name">积分</div>
            <div class="header-tab-interval"></div>
          </div>
          <div class="header-tab-item">
            <coupon2 width="24" height="24" color="#fff"/>
            <div class="item-name">优惠券</div>
            <div class="header-tab-interval"></div>
          </div>
          <div class="header-tab-item">
            <VIP width="24" height="24" color="#fff"/>
            <div class="item-name">VIP会员</div>
          </div>
        </div>
      </div>

      <!-- 弧 以及 深圳城市剪影 -->
      <div class="user-header-arc">
        <img class="user-header-sketch" src="https://ycpduser.oss-cn-shenzhen.aliyuncs.com/wx20/user/sketch-picture.png" />
      </div>
    </div>

    <!-- 爱车 已登录 -->
    <div v-if="loginIofor" class="user-car" @click="jumpToMyCar">
      <div class="car-show">
        <div class="car-show-content">
          <!-- 暂时不显示车型对应logo -->
          <!-- <div class="car-show-logo">
            <img src="http://p6ygud9kn.bkt.clouddn.com/YCPD/wx20/Mercedes-Benz.png" />
          </div> -->
          <div class="car-show-describe">
            <div class="describe-main">{{loginIofor.Brand}}</div>
            <div class="describe-sub">{{loginIofor.CarNo}}</div>
          </div>
          <div class="car-show-other">
            <!-- <div class="other-server">{{loginIofor.Series ? `已服务${loginIofor.Series}次` : '尚未服务'}}</div> -->
            <div class="other-select">
              <icon
                color="#F56C6C"
                width="12"
                height="12"
                name="check-square"
              />
              默认爱车
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- 爱车 未登录 -->
    <div v-else class="user-car">
      <div class="car-add" v-on:click="showNotCompleted('请先登录')">
        <add color="#f8535a" />
        <div class="car-add-describe">添加爱车</div>
      </div>
    </div>

    <!-- 入口合集 -->
    <div class="user-entry-list">
      <div class="entry-list-content">

        <div class="entry-item" v-on:click="jumpToOrder('all')">
          <div class="entry-svg-content">
            <alreadyReserved color="#f8535a" width="26" height="26"/>
          </div>
          <div class="item-name-line1">全部</div>
        </div>
        <div class="entry-item" v-on:click="jumpToOrder('paying')">
          <div class="entry-svg-content">
            <payment2 color="#f8535a" width="30" height="30"/>
          </div>
          <div class="item-name-line1">待支付</div>
        </div>
        <div class="entry-item" v-on:click="jumpToOrder('order')">
          <div class="entry-svg-content">
            <addedServices color="#f8535a"/>
          </div>
          <div class="item-name-line1">已预约</div>
        </div>
        <div class="entry-item" v-on:click="jumpToOrder('evaluate')">
          <div class="entry-svg-content">
            <evaluate2 color="#f8535a" width="26" height="26"/>
          </div>
          <div class="item-name-line1">已评价 </div>
        </div>
        

        <div class="entry-item" v-on:click="jumpToOrder()">
          <div class="entry-svg-content" style="background-color: #fadc1a">
            <financialRecords color="#fff"/>
          </div>
          <div class="item-name">消费记录</div>
        </div>
        <div class="entry-item" v-on:click="showNotCompleted( loginIofor ? '暂未上线' : '请先登录')">
          <div class="entry-svg-content" style="background-color: #df55a2">
            <evaluate color="#fff"/>
          </div>
          <div class="item-name">我的评价</div>
        </div>
        <div class="entry-item" v-on:click="showNotCompleted( loginIofor ? '暂未上线' : '请先登录')">
          <div class="entry-svg-content" style="background-color: #3eb7fc">
            <invoice color="#fff"/>
          </div>
          <div class="item-name">我的发票</div>
        </div>
        <div class="entry-item" v-on:click="showNotCompleted( loginIofor ? '暂未上线' : '请先登录')">
          <div class="entry-svg-content" style="background-color: #0ccaca">
            <collection color="#fff"/>
          </div>
          <div class="item-name">我的收藏</div>
        </div>

      </div>
    </div>

    <!-- 提示栏 -->
    <div class="user-attention" v-on:click="callService">
      <div class="attention-item main-flex-start">
        <icon style="width: 18px; height: 18px;">
          <icon name="exclamation" style="fill: #f44336;"/>
          <icon name="circle-o" scale="2" style="fill: #f44336;"/>
        </icon>
        <div>咨询服务热线: <a>400-110-6558</a></div>
      </div>
    </div>

    <!-- 底部 TabBar -->
    <tabbar 
      :selectIndex="2"
      :callbackFun="tabbarClick"
    />
  </div>
</template>

<script>

// mint-ui 框架
import Vue from 'vue';
import { Toast } from 'mint-ui';
import 'mint-ui/lib/toast/style.css';

// vue-awesome
import icon from 'vue-awesome/components/Icon';
import 'vue-awesome/icons/angle-right';
import 'vue-awesome/icons/exclamation';
import 'vue-awesome/icons/circle-o';
import 'vue-awesome/icons/check-square';

// 自己封装的组件
import tabbar from '@/components/TabBar.vue';

import ajaxs from './ajaxs.js';

export default {
  name: 'user',

  components: {
    // 自写组件
    tabbar,
    // vue-awesome
    icon,
  },

  data () {
    return {
      pictures: { // 所有图片
        citySketch: require('./../../assets/sketch-picture.png'), // 城市剪影
      },

      locationhost: window.location.host
    }
  },

  computed: {
    loginIofor() { // 用户信息 
      return this.$store.getters.getLoginIofor
    },

    openid() {
      // 为什么不能通过 getters getLoginIofor 带出 openid?
      // 因为 即使未登录 openid 也是存在的 
      return this.$store.state.user.openid
    },

    userRelated() { // 用户积分 优惠券 会员
      let VIP = {
        '1': '黄金会员',
        '2': '铂金会员',
        '3': '钻石会员',
        '0': '会员'
      }

      let related = {
        points: this.$store.state.user.points, // 用户积分
        VIP: { // VIP会员
          grade: this.$store.state.user.VIP.grade,
          name: VIP[this.$store.state.user.VIP.grade]
        }
      }
      return related
    },
  },

  methods: {
    /**
     * 跳转到登录页面
     */
    jumpToLogin() {
      let openid = this.$store.state.user.openid;
      
      // 判断顶部是否存在 openid
      if (!openid) {
        openid = window.localStorage.openid;
      }

      window.location.href = `http://${window.location.host}/wx20/register/index.html#/index/${openid}/`;
    },

    /**
     * 跳转到车辆中心
     */
    jumpToMyCar() {
      window.location.href = `http://${window.location.host}/wx20/register/index.html#/mycar/${this.loginIofor.CustomerID}/2/3/4`;
      
    },

    tabbarClick(selectIndex) { // 底部 tabbar 点击触发
      if (selectIndex === 'home') { // 如果 标识为 home 则跳转到 主页
        this.$router.push({path:'/home'});
      }
    },

    callService() { // 呼叫客服
      window.location.href = 'tel://4001106558';
    },

    jumpToOrder(navbarSelected) { // 跳转客服
		// if (this.loginIofor) { // 已经登录

		// 	if (navbarSelected) { // 顶部选项卡
		// 		localStorage.setItem('userOrderSelected', navbarSelected);
		// 	}
		// 	this.$router.push('/user/order');
		// } else {
		// 	Toast({
		// 		message: '请登录',
		// 		duration: 1000
		// 	});
		  // }
		  this.$router.push({
			  path:'/reservationList'
		  })
    },

    jumpToUrl(url) { // 根据 url 进行跳转
      window.location.href = url;
    },

    showNotCompleted(message) { // 弹出提示
      Toast({
        message: message ? message : '升级中',
        duration: 1000
      });
    }
  },
}

</script>

<style scoped lang="less">

.main-flex-start {
  display: -webkit-box;  /* 老版本语法: Safari, iOS, Android browser, older WebKit browsers. */
  display: -moz-box;     /* 老版本语法: Firefox (buggy) */
  display: -ms-flexbox;  /* 混合版本语法: IE 10 */
  display: -webkit-flex; /* 新版本语法: Chrome 21+ */
  display: flex;         /* 新版本语法: Opera 12.1, Firefox 22+ */
  justify-content: flex-start;
}

.user {
  width: 100%;
  min-height: 100%;
  background: #efefef;
  overflow: hidden;
}

// 头部
.user .user-header {
  position: relative;
  width: 100%;
  height: 170px;
  background: #b71c1c;

  .user-header-main {
    position: relative;
    height: 170px;
    z-index: 1;

    .headphones-content {
      padding-top: 10px;
      padding-right: 15px;
      text-align: right;
    }

    .header-login {
      display: -webkit-box;  /* 老版本语法: Safari, iOS, Android browser, older WebKit browsers. */
      display: -moz-box;     /* 老版本语法: Firefox (buggy) */
      display: -ms-flexbox;  /* 混合版本语法: IE 10 */
      display: -webkit-flex; /* 新版本语法: Chrome 21+ */
      display: flex;         /* 新版本语法: Opera 12.1, Firefox 22+ */
      align-items: center;
      justify-content: flex-start;
      padding-left: 15px;

      .login-portrait {
        width: 50px;
        height: 50px;
        border-radius: 25px;
        background: #f2f6f9;
        text-align: center;
        overflow: hidden;

        img {
          width: 100%;
          height: 100%;
        }

        .personnel {
          padding: 4px;
        }
      }

      .login-content {
        padding-left: 15px;
        color: #fff;
      }

      .login-icon {
        padding-left: 15px;

        svg {
          position: relative;
          top: 2.5px;
        }
      }
    }

    .header-tab {
      width: 100%;
      position: absolute;
      bottom: 0px;
      color: #fff;

      .header-tab-item {
        position: relative;
        font-size: 14px;
        width: 33.33%;
        text-align: center;

        .header-tab-interval {
          position: absolute;
          top: 0px;
          right: 0px;
          height: 100%;
          width: 1px;
          background: #fff;
        }
      }
    }
  }

  .user-header-arc {
    overflow: hidden;
    position: absolute;
    bottom: -30px;
    left: 50%;
    margin-left: -350px;
    height: 210px;
    width: 700px;
    background-color: #b71c1c;
    border-radius: 100%;
    -o-border-radius: 100%;
    -ms-border-radius: 100%;
    -moz-border-radius: 100%;
    -webkit-border-radius: 100%;

    .user-header-sketch {
      position: absolute;
      height: 170px;
      width: 700px;
      bottom: 0px;
      opacity: 0.1;
    }
  }
}

// 爱车
.user .user-car {
  padding-top: 45px;
  padding-bottom: 15px;
  background: #fff;
  border-bottom: 1px solid #ddd;

  // 未登录
  .car-add {
    margin: 0 auto;
    width: 60%;
    padding: 15px;
    background: #f2efea;
    border-radius: 5px;
    text-align: center;

    .car-add-describe {
      color: #f8535a;
    }
  }

  // 已登录
  .car-show {
    margin: 0 auto;
    width: 70%;
    background: #f2efea;
    border-radius: 5px;

    .car-show-content {
      display: -webkit-box;  /* 老版本语法: Safari, iOS, Android browser, older WebKit browsers. */
      display: -moz-box;     /* 老版本语法: Firefox (buggy) */
      display: -ms-flexbox;  /* 混合版本语法: IE 10 */
      display: -webkit-flex; /* 新版本语法: Chrome 21+ */
      display: flex;         /* 新版本语法: Opera 12.1, Firefox 22+ */
      align-items: center;
      justify-content: flex-start;
      min-height: 72px;

      .car-show-logo {
        padding-top: 15px;
        padding-left: 15px;
        padding-bottom: 15px;
        width: 42px;
        height: 42px;
        img {
          width: 100%;
          height: 100%;
        }
      }

      .car-show-describe {
        padding-left: 15px;

        .describe-main {
          font-size: 14px;
          color: #303133;
          line-height: 22px;
        }
        .describe-sub {
          font-size: 12px;
          color: #606266;
        }
      }
      .other-server {
        position: relative;
        padding-right: 15px;
        top: -5px;
        text-align: right;
        color: #606266;
        font-size: 12px;
      }

      .car-show-other {
        position: relative;
        flex: 1;
        height: 42px;
        .other-select {
          position: absolute;
          color: #303133;
          bottom: -5px;
          font-size: 12px;
          right: 15px;
          border-bottom: 0px;
          svg {
            position: relative;
            top: 1px;
          }
        }
      }
    }
  }
}

// 入口合集
.user .user-entry-list {
  margin-top: 15px;
  border-top: 1px solid #ddd;
  border-bottom: 1px solid #ddd;
  margin-bottom: 15px;
  background: #fff;

  .entry-list-content {
    padding-top: 15px;
    position: relative;
    overflow: hidden;

    .entry-item {
      padding-bottom: 15px;
      width: 25%;
      float: left;
      text-align: center;

      .entry-svg-content {
        display: -webkit-box;  /* 老版本语法: Safari, iOS, Android browser, older WebKit browsers. */
        display: -moz-box;     /* 老版本语法: Firefox (buggy) */
        display: -ms-flexbox;  /* 混合版本语法: IE 10 */
        display: -webkit-flex; /* 新版本语法: Chrome 21+ */
        display: flex;         /* 新版本语法: Opera 12.1, Firefox 22+ */
        align-items: center;
        justify-content: center;
        margin: 0 auto;
        width: 44px;
        height: 44px;
        border-radius: 20px;
      }

      .item-name-line1 {
        font-size: 14px;
        line-height: 22px;
        color: #606266;
      }

      .item-name {
        padding-top: 10px;
        font-size: 14px;
        line-height: 22px;
        color: #606266;
      }
    }
  }
}

// 提示栏
.user .user-attention {
  border-top: 1px solid #ddd;
  border-bottom: 1px solid #ddd;
  background: #fff;

  .attention-item {
    padding: 10px;
    font-size: 14px;
    line-height: 20px;
    color: #909399;

    > svg {
      position: relative;
      top: 1px;
      padding-right: 5px;
    }

    a {
      color: #409EFF;
    }
  }
}

</style>
