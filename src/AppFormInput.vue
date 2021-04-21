<template>
<form class="card card-w30" @submit.prevent="submitHandler">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="blockType">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
      </div>
      <div class="form-control">
        <label for="value">Значение</label>
        <textarea 
          id="value" 
          rows="3"
          v-model="value"
          
         ></textarea>
      </div>
      
      
      <button :disabled="!isValid" class="btn primary">Добавить</button>
    </form>
    

</template>

<script>
export default {
  data() {
    return {
      blockType: 'title',
      value: '',

    }
  },
    emits: ['add-blocks'],
    props: {
        blocks: Array
    },
    methods: {  
      submitHandler() {
         this.$emit('add-blocks', {
           blockType: this.blockType,
           value: this.value,
           id: Date.now()
         }
         )
         this.value = ''
         this.blockType = 'title'
      },
     
     
    },
    computed: {
         isValid() {
        return this.value.length > 3
      }
    }

}
</script>

<style>

</style>