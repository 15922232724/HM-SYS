
<template>
  <div>
    <el-card class="box-card">
      <el-tabs type="card" v-model="extend">
        <el-tab-pane label="中介" name="first">
          <el-collapse>
            <el-collapse-item>
              <template slot="title">
                <img src="/img/map/extend.png" width="20px" height="20px" />
                <p>高级筛选</p>
              </template>
              <search :type="type"></search>
            </el-collapse-item>
          </el-collapse>
          <div class="switch">
            <img src="/img/map/Intermediary.jpg" class="mapImgLengend" />

            <switch-button :type="type" @showMapInfo="showMapInfo" class="switchButton"></switch-button>
          </div>
        </el-tab-pane>
      </el-tabs>
    </el-card>
  </div>
</template>
<script>
import search from './components/search'
import switchButton from './components/switch'

import { IntermediaryHandle } from '../../../../class/map/handle/iconsHandle/extend/Intermediary'
export default {
  name: 'iconHouse',
  data () {
    return {
      value: false,
      map: {},
      extend: 'first',
      type: 'Intermediary'
    }
  },
  components: {
    search,
    switchButton
  },
  inject: ['mapDom'],

  mounted () {
    this.map = this.$store.state.defaultMap
  },
  methods: {
    showMapInfo (info) {
      if (info) {
        this.IntermediaryHandle = new IntermediaryHandle(this.mapDom.map, 'Intermediary')
        this.IntermediaryHandle.show(info)
      } else {
        this.IntermediaryHandle.hidden()

      }
    },
  }

}
</script>
<style >
</style>
