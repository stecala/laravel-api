<template>
    <div>
        <header>
            <div class="container-lg py-3">
                <div class="row justify-content-between align-items-center">
                    <div class="col-3">
                        <h1>
                            Boolpress
                        </h1>
                    </div>
                    <div class="col-6">
                        <input type="text" placeholder="filtro elementi nel post" @keyup.enter="ApiCallFilterPosts()" v-model="search">
                    </div>
                    <div class="col-2">
                        <a href="http://127.0.0.1:8000/admin" class="btn btn-info">Backoffice</a>
                    </div>
                </div>
            </div>
        </header>
        <main>
            <PostComponent v-for="post in posts" :key="post.id" :post='post'  class="my-5"/>
        </main>
    </div>
</template>

<script>
import PostComponent from './PostComponent.vue';
import axios from 'axios';
export default {
    components:{
        PostComponent,
    },
    data: function(){
        return{
            posts: [],
            search: null,
        }
    },
    methods: {
    //! creo una funzione per effetuare la chiamata API
        ApiCallPosts(){
            axios.get('/api/posts')
            .then((result)=>{
                this.posts=result.data.results.data.data
                console.log(result.data.results)
            })
            .catch((error)=>{
                console.error(error)
            })
        },
        ApiCallFilterPosts(){
            axios.get('/api/posts?description=' + this.search)
            .then((result)=>{
                this.posts=result.data.results.data.data
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

<style lang="scss" scoped> 
    header{
        box-shadow: 5px 0 10px rgba(0, 0, 0, 0.527);
        position: fixed;
        width: 100%;
        background-color: white;
        z-index: 2;
    }
    main{
        padding-top: 105px;
    }
</style>