<template>
  <div class="row q-mb-sm">
    <q-input
      autofocus
      clearable
      outlined
      v-select-all
      :value="name"
      @input="$emit('update:name', $event)"
      class="col"
      ref="name"
      :rules="[val => !!val || 'Field is required']"
      label="Task name"/>
  </div>
</template>

<script>
import {selectAll} from "src/directives/directive-select-all";

export default {
  props: ['name'],
  directives: {
      selectAll
  }
}
</script>

<style scoped>

</style>
