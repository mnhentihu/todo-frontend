<template>
    <main class="w-full font-mono bg-gradient-to-tr from-cyan-300 via-blue-300 to-purple-400">
        <div class="m-auto w-3/4 h-screen flex flex-row gap-4 justify-between items-center ">
            <div
                class="profile w-1/2 h-2/3 bg-slate-100 rounded-l-2xl p-2 flex flex-col items-center justify-center gap-8 shadow-slate-500 shadow-xl">
                <div class="flex flex-col items-center">
                    <h1 class="text-lg font-bold">Username</h1>
                    <span class="text-md">E-Mail</span>
                </div>
                <form class="w-full flex flex-col gap-2" @submit.prevent="submitForm">
                    <input type="text" v-model="formData.title" placeholder="Title" class="border border-slate-600 p-2">
                    <textarea id="w3review" v-model="formData.description" name="w3review" rows="4" cols="50"
                        placeholder="Description" class="border border-slate-600 p-2"></textarea>
                    <button class="shadow-slate-500 shadow-xl w-full rounded-lg bg-slate-300 h-auto hover:bg-slate-400">Add
                        TODO</button>
                </form>
            </div>
            <div class="todo-list w-full h-2/3 bg-slate-100 rounded-r-2xl p-6 shadow-slate-500 shadow-xl  overflow-y-auto">
                <div class="">
                    <h1 class="text-center font-black text-2xl underline">TODO List</h1>
                    <hr class="border-b border-dashed border-slate-500 my-3">
                </div>
                <ul class="h-full">
                    <li v-for="todo in fix" v-bind:key="todo.id">
                        <div class="flex flex-col">
                            <div class="flex flex-row">
                                <span class="w-2/3 max-w-full text-wrap h-10 max-h-10 leading-tight font-bold">{{
                                    todo.title
                                }}</span>
                                <span class="w-1/3 text-right">{{ todo.status }}</span>
                            </div>
                            <p class="w-full text-wrap text-xs ">{{ todo.description }} </p>
                        </div>
                        <hr class="border-b-0 border-slate-400 my-1 ">
                    </li>
                </ul>
            </div>
        </div>
    </main>
</template>

<script setup>
useHead({
    title: 'TODO - List',
})

const { data: todos } = await useFetch('http://localhost:8000/api/todo')
const fix = todos.value.data

const formData = ref({
    id_user: 1,
    title: '',
    description: '',
    status: 'TODO',
})

const submitForm = async () => {
    const { data: responseData } = await useFetch('http://localhost:8000/api/todo', {
        method: 'post',
        body: {
            id_user: formData.value.id_user,
            title: formData.value.title,
            description: formData.value.description,
            status: formData.value.status,
        }
    })
    console.log(responseData.value)
    window.location.reload(true)
}

</script>