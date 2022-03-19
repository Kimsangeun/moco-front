<template>
  <div class="party-list-wrap">
    <div v-for="item in list" :key="item.id" class="party-card">
      <el-card>
        <div slot="header" class="party-card-header">
          <div class="status">
            <span class="status-icon" :class="`status-${item.status}`">{{ statusName(item.status) }}</span>
          </div>
          <div class="title">{{ item.title }}</div>
        </div>
        <div class="list-item-wrap">
          <ul>
            <li>
              <div>날짜:</div>
              <div>{{ item.party_date_str }}</div>
            </li>
            <li>
              <div>인원수:</div>
              <div>{{ `${item.user_num} / ${item.max_num}` }}</div>
            </li>
            <li>
              <div>시간:</div>
              <div>{{ item.time_str }}</div>
            </li>
            <li>
              <div>장소:</div>
              <div>{{ item.location }}</div>
            </li>
          </ul>
        </div>
        <div class="tag-wrap">
          <span v-for="tag in item.tag_list" :key="tag" class="tag-icon">
            {{ tag }}
          </span>
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
          title: '파이썬 프로젝트 하시죠~파이썬 프로젝트 하시죠~파이썬 프로젝트 하시죠~파이썬 프로젝트 하시죠~파이썬 프로젝트 하시죠~',
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
          id: 1,
          status: 'a',
          title: '파이썬 프로젝트 하시죠~',
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
            'mysql',
            'vuejs'
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
            'python',
            'mysql',
            'vuejs'
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
            'python',
            'mysql',
            'vuejs'
          ]
        }
      ]
    }
  },
  methods: {
    statusName(value) {
      const name = value === 'a' ? '모집중' : value === 'b' ? '진행중' : '진행완료'
      return name
    }
  }
}
</script>
