<template>
 
    <section class="bg-white dark:bg-gray-900">
        <div class="container flex flex-col items-center px-4 py-12 mx-auto text-center">
            <h2 class="text-3xl font-semibold tracking-tight text-gray-700 sm:text-4xl dark:text-white">
                counter<br> {{counter}} <sup>2</sup> {{SquareCounter}}
            </h2>
            
            <div class="mt-6 sm:-mx-2">
                <div class="inline-flex w-full sm:w-auto sm:mx-2">
                    <button @click="decrement" class="inline-flex items-center justify-center w-full px-5 py-2 text-white bg-blue-600 rounded-lg hover:bg-blue-500 focus:ring focus:ring-blue-300 focus:ring-opacity-80">
                       Decrement
                    </button>
                </div>

                <div class="inline-flex w-full mt-4 sm:w-auto sm:mx-2 sm:mt-0">
                    <button @click="increment" class="inline-flex items-center justify-center w-full px-5 py-2 text-gray-700 transition-colors duration-150 transform bg-white border border-gray-200 rounded-lg dark:bg-gray-900 dark:border-gray-700 hover:bg-gray-100 dark:text-white sm:w-auto dark:hover:bg-gray-800 dark:ring-gray-700 focus:ring focus:ring-gray-200 focus:ring-opacity-80">
                        Increment
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
   data() {
    return {
        counter: 5,
    }
   },
   methods: {
    getSquareValue(){

    },
     increment(){
        this.counter++
      },
      decrement(){
        this.counter--
      }
   },

   computed: {
    SquareCounter(){
      return this.counter *  this.counter
    }
   }
   
    


}
</script>

<style>

</style>