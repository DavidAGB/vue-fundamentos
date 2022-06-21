<template>
        
        <div v-if="img">
          <img  alt="Vue logo" class="logo" :src="img" width="200" height="200" />
        </div>
        
      
        <div class="bg-dark">

        </div>

        <div class="container">
         <input type="text" v-model="question" placeholder="hazme una pregunta">

         <div v-if="isValidQuestion">
            <h3>{{question}}</h3>
            <h3>{{ answer}}</h3>


         </div>
        </div>

 
</template>

<script>
export default {
    //watch 
    //observar cambios en una propiedad reactiva

    data() {
        return {
            question: null,
            answer: null,
            img: null,
            isValidQuestion:false
        }
    },

    methods: {
        async getAnswer(){
           this.answer = "Pensando..."

          const {answer, image} =  await fetch('https://yesno.wtf/api').then(r => r.json())
        
           this.answer = answer
           this.img = image
        }
    },

    watch: {
        question(value,oldValue) {
            this.isValidQuestion = false
            if (!value.includes('?'))  return
            this.isValidQuestion = true
            this.getAnswer();
          
        }

    }

}
</script>

<style>

</style>