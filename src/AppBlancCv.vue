<template>
    <div class="card card-w70">
      <template v-if="blocks.length">
        <component 
        v-for="block in blocks"
        :key="block.id"
        :is="'app-'+ block.blockType"
        v-bind="{value: block.value}"
        >
        </component>
      </template>
      <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
    </div>
</template>

<script>
  import AppTitle from './parts/AppTitle'
  import AppSubtitle from './parts/AppSubtitle'
  import AppText from './parts/AppText'
  import AppAvatar from './parts/AppAvatar'

  export default {
    props: {
      blocks: Array,
      value: {
        type: String,
        required: true
      },
      blockType: {
        type: String,
        required: true
      }
    },
    components: {AppTitle, AppSubtitle, AppAvatar, AppText}
  }
</script>

<style>

</style>