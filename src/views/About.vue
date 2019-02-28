<template>
  <div class="about">
    <h3>mint study</h3>
    <p>load lazy</p>
    <!--!!! 待实现-->
    <p>range</p>
    <mt-range
      v-model="rangeValue"
      :min="10"
      :max="90"
      :step="10"
      :bar-height="5">
      <div slot="start">10</div>
      <div slot="end">90</div>
    </mt-range>
    <p>progress</p>
    <mt-progress :value="20" :bar-height="5">
      <div slot="start">0%</div>
      <div slot="end">100%</div>
    </mt-progress>
    <p>picker</p>
    <mt-picker :slots="slots" @change="onValuesChange"></mt-picker>
    <p>date time picker</p>
    <button type="button" @click="openPicker()">time picker</button>
    <mt-datetime-picker
      ref="picker"
      type="time">
    </mt-datetime-picker>
    <p>index list</p>
    <mt-index-list :height="500">
      <mt-index-section index="A">
        <mt-cell title="Aaron"></mt-cell>
        <mt-cell title="Alden"></mt-cell>
        <mt-cell title="Austin"></mt-cell>
      </mt-index-section>
      <mt-index-section index="B">
        <mt-cell title="Baldwin"></mt-cell>
        <mt-cell title="Braden"></mt-cell>
      </mt-index-section>
      <mt-index-section index="Z">
        <mt-cell title="Zack"></mt-cell>
        <mt-cell title="Zane"></mt-cell>
      </mt-index-section>
    </mt-index-list>
    <p>platte button</p>
    <mt-palette-button content="+" @expand="main_log('expand')" @expanded="main_log('expanded')" @collapse="main_log('collapse')"
                       direction="rt" class="pb" :radius="80" ref="target_1" mainButtonStyle="color:#fff;background-color:#26a2ff;"
                       style="left:30px;">
      <div class="my-icon-button indexicon icon-popup" @touchstart="sub_log(1)"></div>
      <div class="my-icon-button indexicon icon-popup" @touchstart="sub_log(2)"></div>
      <div class="my-icon-button indexicon icon-popup" @touchstart="sub_log(3)"></div>
    </mt-palette-button>
    <p>header</p>
    <mt-header fixed title="标题拉拉">
      <router-link to="/" slot="left">
        <mt-button icon="back">返回</mt-button>
      </router-link>
      <mt-button icon="more" slot="right"></mt-button>
    </mt-header>
  </div>
</template>

<script>
export default {
  name: 'about',
  data () {
    return {
      rangeValue: 20,
      slots: [
        {
          flex: 1,
          values: ['2015-01', '2015-02', '2015-03', '2015-04', '2015-05', '2015-06'],
          className: 'slot1',
          textAlign: 'right'
        }, {
          divider: true,
          content: '-',
          className: 'slot2'
        }, {
          flex: 1,
          values: ['2015-01', '2015-02', '2015-03', '2015-04', '2015-05', '2015-06'],
          className: 'slot3',
          textAlign: 'left'
        }
      ]
    }
  },
  methods: {
    onValuesChange(picker,values) {
      if (values[0] > values[1]) {
        picker.setSlotValue(1,values[0])
      }
    },
    openPicker () {
      this.$refs.picker.open();
    },
    main_log(val) {
      console.log('main_log', val);
    },
    sub_log(val) {
      console.log('sub_log', val);
      this.$refs.target_1.collapse();
    }

  }
}
</script>
