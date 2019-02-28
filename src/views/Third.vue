<template>
    <div class="third">
      <h3>Third</h3>
      <mt-tabbar v-model="selectedT" :fixed="true">
        <mt-tab-item id="外卖">
          <img slot="icon" src="../assets/logo.png">
          外卖
        </mt-tab-item>
        <mt-tab-item id="发现">
          <img slot="icon" src="../assets/logo.png">
          发现
        </mt-tab-item>
        <mt-tab-item id="我的">
          <img slot="icon" src="../assets/logo.png">
          我的
        </mt-tab-item>
      </mt-tabbar>

      <mt-navbar v-model="selectedT">
        <mt-tab-item id="外卖">选项一</mt-tab-item>
        <mt-tab-item id="发现">选项二</mt-tab-item>
        <mt-tab-item id="我的">选项三</mt-tab-item>
      </mt-navbar>

      <!-- tab-container -->
      <mt-tab-container v-model="selectedT">
        <mt-tab-container-item id="外卖">
          <mt-cell v-for="n in 3" :title="'内容 ' + n" />
        </mt-tab-container-item>
        <mt-tab-container-item id="发现">
          <mt-cell v-for="n in 3" :title="'测试 ' + n" />
        </mt-tab-container-item>
        <mt-tab-container-item id="我的">
          <mt-cell v-for="n in 3" :title="'选项 ' + n" />
        </mt-tab-container-item>
      </mt-tab-container>

      <div>
        <mt-button type="default">default</mt-button> |
        <mt-button type="primary">primary</mt-button> |
        <mt-button type="danger">danger</mt-button>
      </div>
    </div>
</template>

<script>
  export default {
    name: 'Third',
    data () {
      return {
        selectedT: '外卖',
        selectedN: 1
      }
    },
    watch: {
      selectedT: function (val, oldVla) {
        console.log(val)
      }
    }
  }
</script>

<style scoped>

</style>
