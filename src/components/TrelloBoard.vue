<script setup lang="ts">

import {ref} from "vue";

import type {Column} from '@/types'; 


const colums = ref<Array<Column>>( [

  {

      id: 1,
      
      title: 'Upcoming',

      tasks: [
        {
            id: 1,

            title: 'créer une appli front',

            content: 'Développer une application avec Vue 3 et API Composition'
        },
        {
            id: 2,

            title: 'créer une appli back',

            content: 'Développer une application avec Laravel 11'
        }
      ]
      },  

      {

id: 2,

title: 'ToDo',

tasks: [

]
},  

{

id: 3,

title: 'Done',

tasks: [

]
}  

])

</script>



<template>


<div class="flex items-start space-x-4">

    <div v-for="column in colums" class="bg-gray-50 rounded shadow-orange-50 min-w-[250px] p-5">

        <header class="font-bold mb-5">{{ column.title }}</header>

        <div v-for="task in column.tasks" class="bg-white rounded shadow min-w-[250px] p-2 mb-2" :title="task.content">
            {{ task.title }}
        </div>
        
    </div>

</div>



</template>




<style scoped>

</style>