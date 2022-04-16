<template>
  <div class="search-wrap" :class="{'is-active': showDetail}">
    <el-input v-model="search" placeholder="검색어를 입력해주세요." class="search-input">
      <el-button slot="append" icon="el-icon-search" />
      <el-button slot="append" @click="openDetail()">상세옵션 <i class="el-icon-arrow-down" /></el-button>
    </el-input>
    <div v-show="showDetail" class="search-detail">
      <el-row>
        <el-col class="detail-title">
          <span>진행상태</span>
        </el-col>
        <el-col class="detail-contents">
          <div>
            <el-checkbox-group
              v-model="detail.statusCheckList"
              class="detail-status"
            >
              <el-checkbox label="A">모집중</el-checkbox>
              <el-checkbox label="B">진행중</el-checkbox>
              <el-checkbox label="C">진행완료</el-checkbox>
            </el-checkbox-group>
          </div>
        </el-col>
      </el-row>
      <el-row>
        <el-col class="detail-title">
          <span>해시태그</span>
        </el-col>
        <el-col class="detail-contents">
          <el-autocomplete
            v-model="detail.hashtag"
            :fetch-suggestions="querySearch"
            placeholder="Please Input Hash-Tag"
            :trigger-on-focus="false"
            size="mini"
            prefix-icon="el-icon-search"
            class="inline-input"
            @select="handleSelect()"
          />
          <div class="tag-wrap">
            <el-tag
              v-for="(tag, index) in detail.tagList"
              :key="index"
              closable
              size="mini"
              style="width:auto; margin-right:10px;"
              @close="closeTag(index)"
            >
              {{ tag }}
            </el-tag>
          </div>
        </el-col>
      </el-row>
      <el-row>
        <el-col class="detail-title">
          <span>지역</span>
        </el-col>
        <el-col class="detail-contents">
          <el-button class="map-btn" icon="el-icon-map-location" />
          <span class="detail-location">{{ detail.location }}</span>
        </el-col>
      </el-row>
      <el-row>
        <el-col class="detail-title">
          <span>날짜</span>
        </el-col>
        <el-col class="detail-contents">
          <el-date-picker
            v-model="detail.date"
            class="detail-date"
            type="daterange"
            range-separator="~"
            start-placeholder="Start date"
            end-placeholder="End date"
            size="mini"
          />
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ListSearch',
  data() {
    return {
      search: '',
      showDetail: false,
      detail: {
        statusCheckList: ['A', 'B', 'C'],
        hashtag: '',
        tagList: ['AWS', 'Vuejs'],
        location: '서울특별시 동작구',
        date: ''
      }
    }
  },
  computed: {
    tags() {
      /* complete inputbox */
      return this.loadAll()
    }
  },
  methods: {
    openDetail() {
      this.showDetail = !this.showDetail
    },
    loadAll() {
      return [
        { 'value': 'aws' },
        { 'value': 'ai' },
        { 'value': 'python' },
        { 'value': 'java' },
        { 'value': 'c++' },
        { 'value': 'vue' },
        { 'value': 'element' },
        { 'value': 'cooking' },
        { 'value': 'mint-ui' },
        { 'value': 'vuex' },
        { 'value': 'vue-route' },
        { 'value': 'vue-router' },
        { 'value': 'babel' }
      ]
    },
    querySearch(queryString, cb) {
      var tags = this.tags
      var results = queryString ? tags.filter(this.createFilter(queryString)) : tags
      // call callback function to return suggestions
      cb(results)
    },
    createFilter(queryString) {
      return (tag) => {
        return (tag.value.toLowerCase().indexOf(queryString.toLowerCase()) === 0)
      }
    },
    handleSelect() {
      if (this.detail.tagList.includes(this.detail.hashtag)) {
        this.$message({
          message: `선택한 해시태그[${this.detail.hashtag}]는 이미 추가된 해시태그입니다.`,
          type: 'error'
        })
      } else {
        this.detail.tagList.push(this.detail.hashtag)
      }
      this.detail.hashtag = ''
    },
    closeTag(index) {
      this.detail.tagList.splice(index, 1)
    }
  }
}
</script>
