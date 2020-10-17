<template>
  <transition
    appear
    enter-active-class="animated zoomIn"
    leave-active-class="animated zoomOut"
  >
    <div
      :class="{'q-mt-lg' : !settings.showTasksInOneList}"
    >
      <list-header
        bgColor="bg-green-4"
        v-if="!settings.showTasksInOneList"
      >Completed
      </list-header>
      <q-list

        bordered
        separator
      >
        <task
          v-for="(task, key) in tasksCompleted"
          :key="key"
          :task="task"
          :id="key"
        ></task>
      </q-list>
    </div>
  </transition>
</template>

<script>

import {mapGetters} from "vuex";

export default {
  props: ['tasksCompleted'],
  computed: {
    ...mapGetters('settings', ['settings'])
  },
  components: {
    'task':
    require('components/Tasks/Task').default,
    'list-header':
    require('components/Shared/ListHeader').default,
  }

}

</script>

<style scoped>

</style>
