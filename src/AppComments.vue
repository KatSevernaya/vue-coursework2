<template>
    <div class="container">
    <p>
      <button class="btn primary" @click="$emit('add-comments')">Загрузить комментарии</button>
      <button class="btn" v-if="comments.length>0" @click="$emit('removeComments')">Удалить Комментарии</button>
    </p>
    <div class="card">
      <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item" 
          v-for="item in comments"
          :key="item.id"
          >
          <div>
            <p><strong>{{ item.email }}</strong></p>
            <small>{{ item.body }}</small>
          </div>
        </li>
      </ul>
    </div>
    
  </div>
</template>

<script>
 
  
  export default {
    data() {
    return {
      
    }
  },
    emits: ['add-comments', 'removeComments'],
    props: ['comments'],
    methods: {
     
    }
   
   
  }
</script>

<style>

</style>