<template>
    <form @submit.prevent="submit">
         <input type="text" placeholder="title" v-model="title">
         <input type="text" placeholder="body" v-model="body">
         <button type="submit">Create</button>
         <hr>
    </form>
</template>

<script>
import { mapMutations } from 'vuex'
export default {
    data() {
        return {
            title: '',
            body: ''
        }
    },
    methods: {
        ...mapMutations(['createPost']),
        submit() {
            this.createPost({
                id: Date.now(),
                title: this.title,
                body: this.body
            });
            this.title = this.body = ''
        }
    }
}
</script>

<style>
input {
    display: block;
    width: 100%;
    border: 1ps solid #ccc;
    border-radius: 2px;
    padding: 10px;
    margin-bottom: 10px;
}
</style>
