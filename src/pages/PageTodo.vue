<template>
  <q-page class="q-pa-md">
    <p>Todo page</p>
    <div class="q-pa-md" style="max-width: 350px">
      <q-list bordered
              separator
      >
      <task
        v-for="(task, key) in tasks"
        :key="key"
        :task="task"
        :id="key"
      ></task>


      </q-list>
    </div>
  </q-page>
</template>

<script>
import {mapGetters} from 'vuex'

export default {
  computed:{
    ...mapGetters('tasks', ['tasks'])
  },
  components:{
    'task': require('components/Tasks/Task').default
  }

}
</script>
<style>

</style>
