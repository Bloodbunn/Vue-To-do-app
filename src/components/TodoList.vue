<template>

<div class="w-[500px] max-[515px]:w-[90%] border border-gray-500 shadow-lg mx-auto mt-10 px-2 py-2 max-sm:">

    <div class="flex justify-between w-full  py-1">
        <input v-model="currentTask" @keyup.enter="addTask" type="text" placeholder="Enter task" class="rounded max-[515px]:text-sm mr-2 w-full py-1 px-3 text-xl border border-gray-200 shadow-sm ">
        <button @click="addTask" class="whitespace-nowrap hover:bg-green-600 rounded-md py-1 px-2 bg-green-500 text-white">Add task</button>

    </div>

    <ul v-for = "(task, index) in tasks" :key="index" class=" w-full py-1 "> 
        <li class="flex justify-between text-center items-center max-[515px]:text-sm border bg-gray-100 rounded-lg border-gray-200 mt-1  text-black px-2 py-2"> 
            {{task}}
            <button @click="removeTask(index)" class="whitespace-nowrap hover:bg-red-700 rounded-md text-sm py-1 px-2 bg-red-500 text-white"> Remove </button>

        </li>
    </ul>
   
</div>

</template>


<script setup>
import {ref} from "vue";

const currentTask = ref('')
const tasks = ref([])
const addTask = () => {
    if (currentTask.value.trim() !== '') { 
        tasks.value.push(currentTask.value)

    }
    currentTask.value = ''

}

const removeTask = (index) => {
    tasks.value.splice(index,1)
}


</script>

