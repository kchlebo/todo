<template>
  <div class="row q-mb-sm">
    <q-input
      autofocus
      clearable
      outlined
      :value="name"
      @input="$emit('update:name', $event)"
      class="col"
      ref="name"
      :rules="[val => !!val || 'Field is required']"
      label="Task name"/>
  </div>
</template>

<script>
export default {
  props: ['name']
}
</script>

<style scoped>

</style>
