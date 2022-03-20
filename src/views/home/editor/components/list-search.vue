<template>
  <div class="search-wrap">
    <el-input placeholder="검색어를 입력해주세요." class="search-input">
      <el-button slot="append" icon="el-icon-search" />
      <el-button slot="append">상세옵션 <i class="el-icon-arrow-down" /></el-button>
    </el-input>
  </div>
</template>

<script>
export default {
  name: 'ListSearch',
  data() {
    return {
      search: ''
    }
  },
  methods: {

  }
}
</script>
