<template>
  <q-page>
    <div class="q-pa-md absolute full-width full-height column">
      <div class="row q-mb-lg">

        <search></search>
        <sort></sort>
      </div>


      <p
        v-if="search && !Object.keys(tasksTodo).length &&
!Object.keys(tasksCompleted).length"
      >No search results</p>

      <q-scroll-area
      class="q-scroll-area-tasks"
      >
        <no-tasks
          v-if="!Object.keys(tasksTodo).length &&
!search"

        ></no-tasks>
        <tasks-todo
          v-if="Object.keys(tasksTodo).length"
          :tasksTodo="tasksTodo"
        ></tasks-todo>

        <tasks-completed
          v-if="Object.keys(tasksCompleted).length"
          :tasksCompleted="tasksCompleted"
          class="q-mb-xl"
        ></tasks-completed>

      </q-scroll-area>

      <div class="absolute-bottom text-center q-mb-lg no-pointer-events">
        <q-btn
          class="all-pointer-events"
          @click="showAddTask = true"
          round
          color="primary"
          size="24px"
          icon="add"
        />
      </div>
    </div>
    <q-dialog v-model="showAddTask">
      <add-task @close="showAddTask = false"></add-task>
    </q-dialog>
  </q-page>
</template>

<script>
import {mapGetters, mapState} from 'vuex'


export default {
  data() {
    return {
      showAddTask: false
    }
  },
  computed: {
    ...mapGetters('tasks', ['tasksTodo', 'tasksCompleted']),
    ...mapState('tasks', ['search'])
  },
  mounted() {
    this.$root.$on('showAddTask', () => {
      this.showAddTask = true
    })
  },
  components: {
    'task': require('components/Tasks/Task').default,
    'add-task': require('components/Tasks/Modals/AddTask').default,
    'tasks-todo': require('components/Tasks/TasksTodo').default,
    'tasks-completed': require('components/Tasks/TasksCompleted').default,
    'no-tasks': require('components/Tasks/NoTasks').default,
    'search': require('components/Tasks/Tools/Search').default,
    'sort': require('components/Tasks/Tools/Sort').default,
  }

}
</script>
<style>
 .q-scroll-area-tasks{
   display: flex;
   flex-grow: 1;
 }
</style>
