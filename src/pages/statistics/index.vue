<template>
  <el-container>
    <el-header height="114px">
      <home-header></home-header>
    </el-header>
    <el-container class="main-wrapper">
      <!-- <el-aside width="200px">Aside</el-aside> -->
      <el-main>
        <el-tabs class="statistics" v-model="activetype" type="border-card">
          <el-tab-pane label="股票统计" name="first">
            <Containter :type="1"></Containter>
          </el-tab-pane>
          <el-tab-pane label="指数统计" name="second">
            <Containter2 :type="0"></Containter2>
          </el-tab-pane>
          <el-tab-pane label="期货统计" name="three">
            <Containter3 :type="0"></Containter3>
          </el-tab-pane>
        </el-tabs>
        <!-- <home-footer></home-footer> -->
      </el-main>
    </el-container>
  </el-container>
</template>
<script>
import HomeHeader from '@/components/HeaderOrder'
import HomeFooter from '@/components/Footer'
import Containter from './components/content.vue'
import Containter2 from './components/index-content.vue'
import Containter3 from './components/futures-content.vue'

export default {
  components: {
    HomeHeader,
    HomeFooter,
    Containter,
    Containter2,
    Containter3
  },
  props: {},
  data () {
    return {
      activetype: 'first'
    }
  },
  watch: {},
  computed: {},
  methods: {},
  created () {
    this.$store.state.activeIndex = 'statistics'
  },
  mounted () {

  }
}
</script>
<style>

</style>
