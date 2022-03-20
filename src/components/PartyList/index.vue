<template>
  <div class="party-list-wrap">
    <div v-for="item in list" :key="item.id" class="party-card">
      <el-card>
        <div slot="header" class="party-card-header">
          <div class="status">
            <el-tag class="status-icon" :class="`status-${item.status}`" :type="statusType(item.status)" size="mini" effect="dark">{{ statusName(item.status) }}</el-tag>
          </div>
          <div class="title">{{ item.title }}</div>
        </div>
        <div class="list-item-wrap">
          <div class="list-item">
            <div>날짜:</div>
            <div>{{ item.party_date_str }}</div>
          </div>
          <div class="list-item">
            <div>인원:</div>
            <div>{{ `${item.user_num} / ${item.max_num}` }}</div>
          </div>
          <div class="list-item">
            <div>시간:</div>
            <div>{{ item.time_str }}</div>
          </div>
          <div class="list-item">
            <div>장소:</div>
            <div>{{ item.location }}</div>
          </div>
        </div>
        <div class="tag-wrap">
          <el-tag v-for="tag in item.tag_list" :key="tag" class="tag-icon" type="info" size="small" effect="plain">{{ tag }}</el-tag>
        </div>
      </el-card>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PartyList',
  data() {
    return {
      list: [
        {
          id: 0,
          status: 'a',
          title: '파이썬 프로젝트 하시죠~파이썬 프로젝트 하시죠~...',
          party_date_str: '2022.04.02 (토)',
          user_num: '1',
          max_num: '6',
          time_str: '11:00 ~ 22:00',
          location: '서울시 은평구',
          tag_list: [
            'python',
            'mysql',
            'vuejs'
          ]
        },
        {
          id: 1,
          status: 'a',
          title: '파이썬 프로젝트 하시죠~파이썬 프로젝트 하시죠~...',
          party_date_str: '2022.04.02 (토)',
          user_num: '1',
          max_num: '6',
          time_str: '11:00 ~ 22:00',
          location: '서울시 동작구',
          tag_list: [
            'python',
            'mysql',
            'vuejs'
          ]
        },
        {
          id: 2,
          status: 'b',
          title: '파이썬 프로젝트 하시죠~',
          party_date_str: '2022.04.02 (토)',
          user_num: '1',
          max_num: '6',
          time_str: '11:00 ~ 22:00',
          location: '서울시 동작구',
          tag_list: [
            'python',
            'mysql'
          ]
        },
        {
          id: 3,
          status: 'b',
          title: '파이썬 프로젝트 하시죠~',
          party_date_str: '2022.04.02 (토)',
          user_num: '1',
          max_num: '6',
          time_str: '11:00 ~ 22:00',
          location: '서울시 동작구',
          tag_list: [
            'Java',
            'oracle',
            'React',
            'AWS'
          ]
        },
        {
          id: 4,
          status: 'c',
          title: '파이썬 프로젝트 하시죠~',
          party_date_str: '2022.04.02 (토)',
          user_num: '1',
          max_num: '6',
          time_str: '11:00 ~ 22:00',
          location: '서울시 동작구',
          tag_list: [
            'Java'
          ]
        }
      ]
    }
  },
  methods: {
    statusName(value) {
      const name = value === 'a' ? '모집중' : value === 'b' ? '진행중' : '진행완료'
      return name
    },
    statusType(value) {
      const type = value === 'a' ? 'success' : value === 'b' ? 'warning' : 'danger'
      return type
    }
  }
}
</script>
