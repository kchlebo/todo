<template>
  <q-page class="q-pa-md">
    <p>Todo page</p>
    <div class="q-pa-md" style="max-width: 350px">
      <q-list bordered
              separator
      >

        <q-item
          v-for="task in tasks"
          :key="task.id"
          @click="task.completed = !task.completed"
          :class="!task.completed ? 'bg-orange-1' : 'bg-green-1'"
          clickable
          v-ripple>
          <q-item-section side top>
            <q-checkbox v-model="task.completed"/>
          </q-item-section>

          <q-item-section>
            <q-item-label
            :class="{ 'text-strikethrough' : task.completed }"
            >
              {{ task.name }}</q-item-label>
          </q-item-section>

          <q-item-section side>
            <div class="row">
              <div class="column justify-center">
                <q-icon name="event"
                        size="18px"
                        class="q-mr-xs"
                />
              </div>
              <div class="column">
                <q-item-label caption
                class="row justify-end"
                >{{ task.dueDate }}</q-item-label>
                <q-item-label
                  class="row justify-end"
                  caption>
                  <small>{{ task.dueTime }}</small>
                </q-item-label>
              </div>
            </div>
          </q-item-section>
        </q-item>

      </q-list>
    </div>
  </q-page>
</template>

<script>

export default {
  data() {
    return {
      tasks: [
        {
          id: 1,
          name: ' Go to shop',
          completed: false,
          dueDate: '2019/05/12',
          dueTime: '18:30'
        },
        {
          id: 2,
          name: ' Get bananas',
          completed: false,
          dueDate: '2019/05/13',
          dueTime: '17:30'
        },
        {
          id: 3,
          name: ' Get apples',
          completed: false,
          dueDate: '2019/05/14',
          dueTime: '16:30'
        }
      ]
    }
  }

}
</script>
<style>

</style>
