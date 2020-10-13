<template>
  <div class="col q-select q-ml-sm">
    <q-select v-model="sortBy"
              :options="options"
              emit-value
              map-options
              class="col"
              filled
              label="Label (stacked)"
              stack-label

    />
  </div>
</template>

<script>
import {mapActions, mapState} from "vuex";

export default {
  data() {
    return {
      options: [
        {
          label: 'Name',
          value: 'name'
        },
        {
          label: 'Date',
          value: 'dueDate'
        }
      ],
    }
  },
  computed:{
    ...mapState('tasks', ['sort']),

    sortBy:{
      get(){
        return this.sort
      },
      set(value){
        this.setSort(value)
      }
    }
  },
  methods:{
    ...mapActions('tasks', ['setSort'])
  }
}
</script>

<style scoped>
.q-select {
  flex: 0 0 112px;
}
</style>
