<template>
  <div class="home">
    <h3>mint study</h3>
    <p>toast</p>
    <button type="button" @click="showToast()">showToast</button>
    <!--<p>indicator 加载提示框 !!!未自动关闭，待解决</p>
    <button type="button" @click="showIndicator()">showIndicator</button>-->
    <!--<p>下拉-上拉 !!! 功能未完成，待解决</p>
    <mt-loadmore :top-method="loadTop" :bottom-method="loadBottom"
                 :bottom-all-loaded="allLoaded" ref="loadmore" :auto-fill="false" :bottom-distance="30">
      <ul>
        <li v-for="(item,index) in list" :key="index">{{item}}</li>
      </ul>
    </mt-loadmore>-->
    <p>Message box</p>
    <button type="button" @click="showAlert()">alert</button>
    <button type="button" @click="showConfirm()">confirm</button>
    <button type="button" @click="showPrompt()">prompt</button>
    <p>action sheet</p>
    <button type="button" @click="actionSheet()">action sheet</button>
    <button type="button" @click="actionSheetWithCancel()">action sheet with cancel</button>
    <mt-actionsheet :actions="actions" cancel-text="" v-model="sheetVisible"></mt-actionsheet>
    <mt-actionsheet :actions="actions" cancel-text="取消文本" v-model="sheetVisibleCancel"></mt-actionsheet>
    <p>popup</p>
    <button type="button" @click="popUpBottom()">popUpBottom</button>
    <button type="button" @click="popUpTop()">popUpTop</button>
    <button type="button" @click="popUpRight()">popUpRight</button>
    <button type="button" @click="popUpLeft()">popUpLeft</button>
    <button type="button" @click="popUpMid()">popUpMid</button>
    <mt-popup v-model="popupVisible" :position="popUpPosition">
      <div>popUp {{popUpPosition}}</div>
    </mt-popup>
    <p>swipe</p>
    <div style="height: 200px">
      <mt-swipe :auto="4000" :show-indicators="true">
        <mt-swipe-item style="background: green">1</mt-swipe-item>
        <mt-swipe-item style="background: red">2</mt-swipe-item>
        <mt-swipe-item style="background: yellow">3</mt-swipe-item>
      </mt-swipe>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import Vue from 'vue'

import { Indicator } from 'mint-ui'
Vue.use(Indicator)

import store from '@/store'

export default {
  name: 'home',
  store,
  data () {
    return {
      toastMsg: 'toast',
      list: [],
      current: '',
      actions: [
        {
          name: 'action01',
          method: this.action01
        },
        {
          name: 'action02',
          method: this.action02
        }
      ],
      sheetVisible: false,
      sheetVisibleCancel: false,
      popupVisible: false,
      popUpPosition: 'bottom'
    }
  },
  methods: {
    showToast () {
      this.$toast({
        message: this.toastMsg,
        duration: 2000,
        position: 'bottom'
      })
    },
    /*showIndicator () {
      this.$indicator.open()
      setTimeout(this.$indicator.close(), 2000)
    },*/
    /*loadTop () {
      console.info("loadTop")
      this.current = 1
      this.list = store.state.lists
      this.$refs.loadmore.onTopLoaded()
    },
    loadBottom () {
      console.info("loadBottom")
    },
    allLoaded () {
      console.info("allLoaded")
    },*/
    showAlert () {
      this.$messagebox.alert('message','title').then(action => {
        console.info("alert")
      })
    },
    showConfirm () {
      this.$messagebox.confirm('message','title').then(action => {
        if (action == 'confirm') {
          console.info('确定')
        }
      }).catch(err => {
        if (err == 'cancel') {
          console.info('取消')
        }
      })
    },
    showPrompt () {
      this.$messagebox.prompt('message').then(({value,action}) => {
        if (action == 'confirm') {
          console.info(action + value)
        }
      }).catch(err => {
        if (err == 'cancel') {
          console.info(err)
        }
      })
    },
    actionSheet () {
      this.sheetVisible = true
    },
    actionSheetWithCancel () {
      this.sheetVisibleCancel = true
    },
    action01 () {
      console.info("action01")
    },
    action02 () {
      console.info("action02")
    },
    popUpBottom () {
      this.popUpPosition = 'bottom'
      this.popupVisible = true
    },
    popUpTop () {
      this.popUpPosition = 'top'
      this.popupVisible = true
    },
    popUpRight () {
      this.popUpPosition = 'right'
      this.popupVisible = true
    },
    popUpLeft () {
      this.popUpPosition = 'left'
      this.popupVisible = true
    },
    popUpMid () {
      this.popUpPosition = ''
      this.popupVisible = true
    }
  }
}
</script>

<style>
  li{
    height: 20px;
  }
</style>
