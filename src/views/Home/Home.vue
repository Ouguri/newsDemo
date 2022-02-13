<template>
  <div class="home-comtainer">
    <!-- 头部 -->
    <van-nav-bar
      title="Ouguri"
      fixed
    />
    <div>{{ artList.length }}</div>
  </div>
</template>

<script>
// 导入request.js
import { getArticleListAPI } from '@/api/articleAPI.js'

export default {
  name: 'Home',
  data() {
    return {
      // 页码值
      page: 1,
      // 每页显示数据条数
      limit: 10,
      artList: []
    }
  },
  methods: {
    // 获取封装文章列表数据的方法
    // 发起get请求获取文章的列表数据
    async initArticleList() {
      const { data: res } = await getArticleListAPI(this.page, this.limit)
      this.artList = res
    }
  },
  created() {
    this.initArticleList()
  }
}
</script>

<style lang="less" scoped>
  .home-comtainer{
    padding: 46px 0 50px 0;
    .van-nav-bar{
      background-color: #007bff;
    }
    /deep/.van-nav-bar__title{
      color:#fff
    }
  }
</style>
