<script setup lang="ts">

import {ref} from "vue";

import type {Column, Task} from '@/types'; 

import TrelloTask from "@/components/TrelloTask.vue";

import Draggable from 'vuedraggable';

import {useLocalStorage} from "@vueuse/core";

const colums = useLocalStorage<Array<Column>>('trello-board', [

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

        <Draggable 
            v-model="colums" 
            group="columns"
            item-key="id"
            :animation="150"
            handle=".cursor-grab"
            class="flex items-start space-x-4"
        >

            <template #item="{element: column } : {element: Column}">
                <div class="bg-gray-50 rounded shadow-orange-50 min-w-[250px] p-5">
                    <div class="flex">
                        <span class="cursor-grab mr-1">💥</span>
                        <header class="cursor-grab font-bold mb-5">{{ column.title }}</header>
                    </div>
                    <Draggable 
                        v-model="column.tasks" 
                        group="tasks"
                        item-key="id"
                    >

                        <template #item="{element: task } : {element: Task}">
                            <TrelloTask :task="task" />
                        </template>

                    </Draggable>

                </div>
            </template>
        </Draggable>

</template>




<style scoped>

</style>