<template>
  <el-container>
    <el-header height="114px">
      <home-header></home-header>
    </el-header>
    <el-container class="main-wrapper">
      <!-- <el-aside width="200px">Aside</el-aside> -->
      <el-main>
        <el-tabs v-model="activetype" type="border-card" @tab-click="handleClick">
          <el-tab-pane label="融资持仓单" name="first">
            <Containter :type="1"></Containter>
          </el-tab-pane>
          <el-tab-pane label="融资平仓单" name="second">
            <Containter2 :type="0"></Containter2>
          </el-tab-pane>
          <el-tab-pane label="指数持仓单" name="three">
            <Containter3 :type="1"></Containter3>
          </el-tab-pane>
          <el-tab-pane label="指数平仓单" name="fours">
            <Containter4 :type="0"></Containter4>
          </el-tab-pane>
          <el-tab-pane label="期货持仓单" name="five">
            <Containter5 :type="1"></Containter5>
          </el-tab-pane>
          <el-tab-pane label="期货平仓单" name="six">
            <Containter6 :type="0"></Containter6>
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
import Containter from './components/table-hold.vue'
import Containter2 from './components/table-sell.vue'
import Containter3 from './components/indextable-hold.vue'
import Containter4 from './components/indextable-sell.vue'
import Containter5 from './components/futurestable-hold.vue'
import Containter6 from './components/futurestable-sell.vue'

export default {
  components: {
    HomeHeader,
    HomeFooter,
    Containter,
    Containter2,
    Containter3,
    Containter4,
    Containter5,
    Containter6
  },
  props: {},
  data () {
    return {
      activetype: 'first'
    }
  },
  watch: {},
  computed: {},
  methods: {
    handleClick () {

    }
  },
  created () {
    this.$store.state.activeIndex = 'holdPositions'
  },
  mounted () {

  }
}
</script>
<style>

</style>
