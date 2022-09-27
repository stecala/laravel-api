<template>
    <div>
        <h1>Posts:</h1>
        <ul>
            <li v-for="post in posts" :key="post.id">
                {{ post.description }}
            </li>
        </ul>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    data: function(){
        return{
            posts: [],

        }
    },
    methods: {
    //! creo una funzione per effetuare la chiamata API
        ApiCallPosts(){
            axios.get('/api/posts')
            .then((result)=>{
                this.posts=result.data.results.data
                console.log(result.data.results)
            })
            .catch((error)=>{
                console.error(error)
            })
        }
    },
    created (){
        this.ApiCallPosts()
    }
}
</script>

<style>

</style>