<template>

<div class="w-[500px] max-[515px]:w-[90%] border border-gray-500 shadow-lg mx-auto mt-10 px-2 py-2 max-sm:">

    <div class="flex justify-between w-full  py-1">
        <input v-model="currentTask" @keyup.enter="addTask" type="text" placeholder="Enter task" class="rounded max-[515px]:text-sm mr-2 w-full py-1 px-3 text-xl border border-gray-200 shadow-sm ">
        <button @click="addTask" class="whitespace-nowrap rounded-md py-1 px-2 bg-green-500 text-white">Add task</button>

    </div>

    <ul v-for = "(task, index) in tasks" :key="index" class=" w-full py-1 "> 
        <li class="flex justify-between text-center items-center max-[515px]:text-sm border bg-gray-100 rounded-lg border-gray-200 mt-1  text-black px-2 py-2"> 
            {{task}}
            <button @click="removeTask(index)" class="whitespace-nowrap rounded-md text-sm py-1 px-2 bg-red-500 text-white"> Remove </button>

        </li>
    </ul>
   
</div>

</template>


<script setup>
import {ref} from "vue";

const currentTask = ref('')
const tasks = ref([])
//trim removes spaces, so here if trim and no letters remain, meaning if we enter just spaces and no letters, it won't add it.
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

<!--
    Sure, let's break down how the `splice` method works in the `removeTask` function:

1. `tasks.value.splice(index, 1);`:
   - `tasks.value` refers to the array of tasks stored in the `tasks` ref.
   - `splice` is a method available on arrays in JavaScript that allows you to modify the contents of an array by removing or replacing existing elements and/or adding new elements in place.
   - In this case, `splice` is used to remove elements from the `tasks` array.
   - The first argument, `index`, specifies the index at which to start modifying the array. It indicates the position of the element to remove.
   - The second argument, `1`, specifies the number of elements to remove starting from the index specified by the first argument. In this case, it's `1`, indicating that only one element should be removed.
   - Therefore, `tasks.value.splice(index, 1);` removes one element from the `tasks` array at the specified `index`.

2. `removeTask(index)`:
   - This function is called when the "Remove" button associated with a task is clicked.
   - The `index` parameter passed to `removeTask` corresponds to the index of the task in the `tasks` array that should be removed.
   - When the button is clicked, it triggers the `removeTask` function with the `index` of the task to be removed.
   - Inside `removeTask`, the `splice` method is used to remove the task from the `tasks` array at the specified index.

In summary, the `removeTask` function uses the `splice` method to remove a task from the `tasks` array based on the index provided. This allows tasks to be removed dynamically when the "Remove" button associated with each task is clicked.
-->