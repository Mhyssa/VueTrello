<script setup lang="ts">

import type {Task} from "@/types";

    defineProps<{

        task: Task,

    }>();

</script>



<template>
        <div class="bg-white rounded shadow min-w-[250px] p-2 mb-2" :title="task.content">

            <input @keyup.enter="($event.target as HTMLInputElement).blur()" v-model="task.title" type="text" /> 

        </div>            
</template>




<style scoped>

</style>