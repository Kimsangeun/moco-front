<template>
  <div class="home-container">
    <list-search />
    <div>
      <party-list />
    </div>
  </div>
</template>

<script>
import ListSearch from './components/list-search'
import PartyList from '@/components/PartyList'

export default {
  name: 'Home',
  components: { ListSearch, PartyList },
  data() {
    return {

    }
  },
  methods: {

  }
}

</script>

<style lang="scss" scoped>

</style>
