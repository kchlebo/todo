<template>
<div class="col">
  <q-input
    bottom-slots
    outlined
    class="col"
    v-model="searchField"
           label="Search"
>
    <template v-slot:append>
      <q-icon v-if="searchField !== ''" name="close" @click="searchField = ''" class="cursor-pointer" />
      <q-icon name="search" />
    </template>
  </q-input>
</div>
</template>

<script>
import {mapActions, mapState} from 'vuex'

export default {

  computed: {
    ...mapState('tasks', ['search']),

    searchField:{
      get() {
        return this.search
      },
      set(value){
        this.setSearch(value)
      }
    }
  },
  methods:{
    ...mapActions('tasks',['setSearch'])
  }
}
</script>

<style scoped>

</style>
