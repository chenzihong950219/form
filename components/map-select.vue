<!--
 * @Description:区域选择
 * @version: 1.0
 * @Author: chenzihong
 * @Date: 2023-05-24 15:41:12
 * @LastEditors: chenzihong
 * @LastEditTime: 2023-05-25 13:46:59
-->
<template>
  <div class="map-select">
    <div class="warp"
      v-if="labels.length"
      @click="add()">

      <div v-for="(item,i) in labels"
        :key="i"
        class="lable">
        {{item[0].toFixed(2)}}，{{item[1].toFixed(2)}}
        <div class="clear"
          @click.stop="clear">清空</div>
      </div>
    </div>

    <div class="add"
      @click="add">
      <i class="iconfont icon-dinwei2 icon-loc"></i>
      添加范围
    </div>
  </div>
</template>
<script>
module.exports = {
  name: 'mapSelect',
  data () {
    return {
      labels: []
    }
  },
  props: {
    value: {
      default () {
        return []
      }
    }
  },
  watch: {
    value: {
      immediate: true,
      deep: true,
      handler (newVal) {
        if (newVal && newVal.length) {
          this.labels = newVal[0]
        } else {
          this.labels = []
        }
      }
    }
  },
  mounted () {

  },
  methods: {
    clear () {
      this.$emit('input', [])
      this.$emit('clear')
    },
    add () {
      this.$emit('add')
    }
  }

}
</script>
<style scoped>
.warp {
  background: #f5f6f7;
  border-radius: 5px;
  max-height: 110px;
  width: 100%;
  overflow-y: auto;
  padding: 10px 0 30px 10px;
  border: 1px solid red;
  position: relative;
}
.clear {
  font-size: 12px;
  color: #198cff;
  position: absolute;
  bottom: 10px;
  right: 10px;
}
.map-select {
  position: relative;
}
.add {
  font-size: 12px;
  color: #198cff;
  position: absolute;
  top: -50px;
  right: 10px;
}
.lable {
  display: inline-block;
  margin-right: 10px;
  background: #eaecee;
  border-radius: 5px;
  padding: 8px;
  margin-bottom: 5px;
}
</style>
