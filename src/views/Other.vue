<template>
    <div id="Other" class="Other">
      <h3>Other</h3>
      <p>mt-cell</p>
      <mt-cell class="mtCell" title="标题" value="说明"></mt-cell>
      <mt-cell class="mtCell" title="回到首页" to="/" is-link></mt-cell>
      <p>cell swipe</p>
      <mt-cell-swipe
        title="cell swipe"
        :right="[
          {
            content: 'Delete',
            style: { background: 'red', color: '#fff' },
            handler: () => this.$messagebox('delete')
           }]">
      </mt-cell-swipe>
      <p>spinner</p>
      <mt-spinner type="snake" color="#26a2ff"></mt-spinner>
      <mt-spinner type="double-bounce" color="#26a2ff"></mt-spinner>
      <mt-spinner type="triple-bounce" color="#26a2ff"></mt-spinner>
      <mt-spinner type="fading-circle" color="#26a2ff"></mt-spinner>
      <p>search</p>
      <mt-search class="mtSearch" v-model="searchValue"></mt-search>
      <p>switch</p>
      <mt-switch v-model="switchValue" slot="开关"></mt-switch>
      <p>checklist</p>
      <!--!!! 选满2个选项后第3个选项仍可点-->
      <mt-checklist
        title="checklist"
        v-model="clValue"
        :options="options"
        :max=2>
      </mt-checklist>
      <p>radio</p>
      <mt-radio title="radio"
                v-model="radioValue"
                :options="radioOps"
                align="right">
      </mt-radio>
      <p>field</p>
      <mt-field label="用户名" placeholder="请输入用户名" v-model="username"></mt-field>
      <mt-field label="邮箱" placeholder="请输入邮箱" type="email" v-model="email"></mt-field>
      <mt-field label="密码" placeholder="请输入密码" type="password" v-model="password"></mt-field>
      <mt-field label="手机号" placeholder="请输入手机号" type="tel" v-model="phone"></mt-field>
      <mt-field label="网站" placeholder="请输入网址" type="url" v-model="website"></mt-field>
      <mt-field label="数字" placeholder="请输入数字" type="number" v-model="number"></mt-field>
      <mt-field label="生日" placeholder="请输入生日" type="date" v-model="birthday"></mt-field>
      <mt-field label="自我介绍" placeholder="自我介绍" type="textarea" rows="4" v-model="introduction"></mt-field>
      <p>badge</p>
      <mt-badge size="small">30</mt-badge>
      <mt-badge size="normal">10</mt-badge>
      <mt-badge size="large">10</mt-badge>
    </div>
</template>

<script>
  export default {
    name: 'Other',
    data () {
      return {
        searchValue: '123',
        switchValue: false,
        clValue: [],
        options: [
          {
            label: '选项A',
            value: '值A',
            disabled: true
          },
          {
            label: '选项B',
            value: '值B'
          },
          {
            label: '选项C',
            value: '值C'
          },
          {
            label: '选项D',
            value: '值D'
          }
        ],
        radioValue:[],
        radioOps:[
          {
            label: '选项A',
            value: 'A'
          },
          {
            label: '选项B',
            value: 'B'
          },
          {
            label: '选项C',
            value: 'C'
          }
        ]
      }
    }
  }
</script>

<style scoped>
#Other {
  text-align: left;
}
.mtSearch {
  height: 50px;
}
</style>
