<template>
  <q-page class="q-pa-md">
    <p>Todo page</p>
    <div class="q-pa-md" style="max-width: 350px">
      <q-list
        v-if="Object.keys(tasks).length"
        bordered
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
    <div class="absolute-bottom text-center q-mb-lg">
      <q-btn
        @click="showAddTask = true"
        round
        color="primary"
        size="24px"
        icon="add"
      />
    </div>
    <q-dialog v-model="showAddTask">
    <add-task @close="showAddTask = false"></add-task>
    </q-dialog>
  </q-page>
</template>

<script>
import {mapGetters} from 'vuex'


export default {
  data(){
    return{
      showAddTask: false
    }
  },
  computed: {
    ...mapGetters('tasks', ['tasks'])
  },
  components: {
    'task': require('components/Tasks/Task').default,
    'add-task': require('components/Tasks/Modals/AddTask').default,
  }

}
</script>
<style>

</style>
