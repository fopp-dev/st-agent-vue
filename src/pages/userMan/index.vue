<template>
  <el-container>
    <el-header height="114px">
      <home-header></home-header>
    </el-header>
    <el-container class="main-wrapper">
      <!-- <el-aside width="200px">Aside</el-aside> -->
      <el-main>
        <ContainterTable></ContainterTable>
        <!-- <home-footer></home-footer> -->
      </el-main>
    </el-container>
  </el-container>
</template>
<script>
import HomeHeader from '@/components/HeaderOrder'
import HomeFooter from '@/components/Footer'
import ContainterTable from './components/table'

export default {
  components: {
    HomeHeader,
    HomeFooter,
    ContainterTable
  },
  props: {},
  data () {
    return {}
  },
  watch: {},
  computed: {},
  methods: {},
  created () {
    this.$store.state.activeIndex = 'userMan'
  },
  mounted () {

  }
}
</script>
<style>

</style>
