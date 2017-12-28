<template>
  <div class="nav">
    <nav>
      <ul>
        <li v-on:click="isshow('1')">
          <div :class="{clicked: clicknum==1}" v-on:click="clicknum=1">cotent1</div>
            <ul class="dropdown" v-on:click="stopfun" v-if="shownum==1">
              <li>asdf</li>
              <li>safsfd</li>
            </ul>
        </li>
        <li v-on:click="isshow('2')">
          <div :class="{clicked: clicknum==2}" v-on:click="clicknum=2">content2</div>
          <ul class="dropdown" v-on:click="stopfun()" v-if="shownum1==1">
            <li>asdf</li>
            <li>safsfd</li>
          </ul>
        </li>
        <li>
          <div :class="{clicked: clicknum==3}" v-on:click="clicknum=3">content3</div>
        </li>
        <li>
          <div :class="{clicked: clicknum==4}" v-on:click="clicknum=4">content4</div>
        </li>
      </ul>
    </nav>
  </div>
</template>
<script>
  export default {
    data () {
      return {
        clicknum: 0,
        shownum: 0,
        shownum1: 0
      }
    },
    methods: {
      isshow (type) {
        switch (type) {
          case '1':
            if (this.shownum == 0) {
              this.shownum = 1
              this.shownum1 = 0
            } else {
              this.shownum = 0
            }
            break
          case '2':
            if (this.shownum1 == 0) {
              this.shownum1 = 1
              this.shownum = 0
            } else {
              this.shownum1 = 0
            }
        }
      },
      stopfun () {
        window.event.cancelBubble = true
      }
    }
  }
</script>
<style lang="less">
  .nav {
    nav {
      padding: 20px 30px;
      .clicked {
        color: #fff;
        background-color: rgba(89, 179, 149, 0.53);
      }
    ;
      & > ul {
        list-style: none;
        &:after {
          content: '';
          width: 0;
          height: 0;
          clear: both;
          display: block;
        }
        & > li {
          float: left;
          animation: leiz 2s infinite;
          @keyframes leiz {
            from {left:0px;}
            to {left:200px;}
          }
          width: 24%;
          margin: 0 .2%;
          position: relative;
          div {
            padding: 10px 0;
            background-color: rgba(128, 128, 128, .2);
          }
          ul {
            list-style: none;
            position: absolute;
            padding: 0;
            box-sizing: border-box;
            margin-top: 5px;
            width: 100%;
            left: 50%;
            margin-left: -105px;
            background-color: rgba(128, 128, 128, .1);
            border: 1px rgba(128, 128, 128, .5) solid;
            li {
              padding: 10px 0;
              &:hover {
                color: yellow;
              }
            }
          }
        }
      }
    }
  }
</style>
