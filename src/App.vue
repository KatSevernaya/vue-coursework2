<template>
  <div class="container column">
    
    <app-form-input
    @add-blocks="addBlock"
   ></app-form-input>
   
   <app-blanc-cv
    :blocks="blocks"
   ></app-blanc-cv>
  </div>
  
  <app-comments
    @add-comments="loadComments"
    @removeComments="removeComments"
    :comments="comments"  
  ></app-comments>
  <app-loader v-if="loading"></app-loader>
  
</template>

<script>
  import AppBlancCv from './AppBlancCv'
  import AppFormInput from './AppFormInput'
  import AppComments from './AppComments'
  import AppLoader from './AppLoader'
  export default {

  data() {
    return {
      blocks: [],
      comments: [],
      loading: false
      
    } 
  },
  methods: {
    addBlock(block) {
      this.blocks.push(block)
    },
    loadComments() {
        this.loading = true
        setTimeout(async () => {
        const response = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42', {
          method: 'GET',
          headers: {
          'Content-Type': 'application/json'
          }
        })
        
          this.comments = await response.json()
        }, 1500 )
        
      },
       removeComments() {
        this.comments = []
        this.loading = false
      }
  },
  components: {AppBlancCv, AppFormInput, AppComments, AppLoader}
}
</script>

<style>
  
</style>
