<template>
    <div class="w-[500px] max-[505px]:w-[90%] mx-auto">
        <h1 class="text-3xl font-bold text-black">Dad Jokes</h1>
        <button @click="fetchJoke" class="p-3 text-sm bg-red-500 hover:bg-red-600 transition-all duration-300 text-white font-bold mt-4 rounded-md">Get Dad Joke</button>
        <p v-if="joke" class="w-full min-h-20  p-3 bg-orange-200 shadow-md mt-4">{{joke}}</p>
    </div>
</template>

<script setup>
import { ref } from "vue";
import axios from 'axios'

const joke = ref(null)

const fetchJoke = async () => {
    try {
        const response = await axios.get("https://icanhazdadjoke.com/", {
            headers: {Accept: "application/json"}
        })
        joke.value = response.data.joke
        
    } catch (error) {
        console.log("Error fetching dad joke: ", error)
        
    }
}

</script>

//install axios (npm i axios)
//THEN and not before: npm run serve