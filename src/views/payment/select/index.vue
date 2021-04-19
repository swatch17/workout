<template>
  <div class="usdt-page">
    <div class="header">
      <div class="header-left">
        <div class="icon-t"><img src="@/assets/images/t.png" /></div>
        <div class="title">USDT</div>
      </div>
      <div><i class="iconfont icon-right"></i></div>
    </div>
    <div class="cell">
      <div class="title">选择主网</div>
      <div class="content">
        <span
          @click="checkItem(i)"
          v-for="(val, i) in ops"
          :class="{
            tab: true,
            item: i == !checkedIndex,
            active: i == checkedIndex,
          }"
          :key="i"
          >{{ val }}<i class="iconfont icon-checked round"></i
        ></span>
      </div>
    </div>
    <div class="cell">
      <div class="title">USDT充值</div>
      <div class="cell-item">
        <div class="time">2020-09-17 18:10:00</div>
        <div class="copy-btn">复制地址</div>
      </div>
      <div class="code-link">0xf593f0858aac475694a48fe88682d1d3fa4419</div>
    </div>
    <div class="box">
      <div class="qr-box">
        <img src="@/assets/images/qr-img.png" alt="" />
        <i class="horn left-top"></i><i class="horn right-top"></i
        ><i class="horn left-bottom"></i><i class="horn right-bottom"></i>
      </div>
      <div class="down-cell">
        <div class="down-btn"><i class="iconfont icon-down"></i>保存二维码</div>
      </div>
    </div>
    <div class="note">
      <div class="note-title">此地址只可接收USDT</div>
      <div class="note-content">
        <p>
          *
          请不要向这个地址充值除USDT之外的资产，任何充入此地址的其他资产将不可找回。
        </p>
        <p>*<span class="times">12</span>此网络确认后上帐。</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PaymentSelect",
  data() {
    return {
      checkedIndex: 0,
      isActive: false,

      ops: ["ERC20", "BEFP2", "BEP20(BSC)"],
    };
  },
  computed: {
    onCheck: function () {
      return `tab active`;
    },
  },
  methods: {
    checkItem: function (a) {
      this.checkedIndex = a;
    },
  },
};
</script>

<style lang="scss">
.usdt-page {
  padding: 10px;
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 30px;
    margin-bottom: 15px;
    &-left {
      display: flex;
      .icon-t {
        img {
          height: 20px;
        }
      }
      .title {
        margin-left: 10px;
      }
    }
    .icon-right {
      font-size: 18px;
      font-weight: 600;
      color: rgba(0, 0, 0, 0.45);
    }
  }
  .cell {
    margin-bottom: 20px;
    font-weight: 500;
    .title {
      margin-bottom: 10px;
      color: rgba(69, 90, 100, 0.6);
    }
    .content {
      display: flex;
      justify-content: space-evenly;
      .tab {
        font-size: 12px;
        padding: 8px 20px;
        border-radius: 4px;
        position: relative;
        .round {
          display: none;
        }
      }
      .item {
        background-color: #f5f5f5;
        border: 1px solid #f5f5f5;
      }
      .active {
        background-color: #fff;
        color: #ffd000;
        border: 1px solid #ffd000;
        .round {
          display: block;
          font-size: 14px;
          height: 12px;
          width: 12px;
          font-weight: 600;
          background-color: #ffd000;
          color: #333;
          border-radius: 50%;
          position: absolute;
          top: -6px;
          right: -6px;
        }
      }
    }
    &-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .time {
      font-size: 12px;
      color: rgba(69, 90, 100, 0.6);
    }
    .copy-btn {
      padding: 8px;
      font-size: 14px;
      color: #999;
      background-color: #f5f5f5;
      border: 1px solid #f5f5f5;
      border-radius: 4px;
    }
  }
  .code-link {
    display: flex;
    justify-content: center;
    font-size: 14px;
    color: #333;
  }
  .box {
    position: relative;

    width: 100%;
    margin-top: 10px;
    border-top: 1px solid #f5f5f5;
    border-bottom: 2px solid #f5f5f5;

    .qr-box {
      margin: 10px auto;
      height: 200px;
      width: 200px;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      img {
        height: 160px;
      }
      .horn {
        height: 30px;
        width: 30px;

        position: absolute;
      }
      .left-top {
        left: 0px;
        top: 0px;
        border-top: 2px solid #f5f5f5;
        border-left: 2px solid #f5f5f5;
      }
      .left-bottom {
        left: 0;
        bottom: 0;
        border-bottom: 2px solid #f5f5f5;
        border-left: 2px solid #f5f5f5;
      }
      .right-top {
        right: 0px;
        top: 0px;
        border-top: 2px solid #f5f5f5;
        border-right: 2px solid #f5f5f5;
      }
      .right-bottom {
        right: 0px;
        bottom: 0px;
        border-right: 2px solid #f5f5f5;
        border-bottom: 2px solid #f5f5f5;
      }
    }
    .down-cell {
      display: flex;
      justify-content: center;
      .icon-down {
        font-weight: 600;
        font-size: 18px;
        margin-right: 5px;
      }
      margin: 20px;
    }
    .down-btn {
      padding: 10px 30px;
      color: #999;
      background-color: #f5f5f5;
    }
  }
  .note {
    margin-top: 20px;
    color: rgba(69, 90, 100, 0.6);
    &-title {
      font-weight: 500;
    }
    &-content {
      font-size: 14px;
      .times {
        color: #ffd000;
      }
    }
  }
}
</style>
