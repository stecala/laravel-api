<template>
    <div class="container-lg card">
      <div class="row">
        <div class="col-12 author">
           <h2 class="">
                {{ post.user.name }}
            </h2>
        </div>
        <div class="img-containter mt-3 mx-auto">
            <img :src="post.img_post" alt="img_post">
        </div>
        <div class="col-12 mt-3">
            <span>{{post.description}}</span>
        </div>
        <div class="col-12 date mt-3">
            {{ post.post_date }}
        </div>
      </div>
    </div>
</template>

<script>
    export default {
        props:{
            post : Object,
        }
    }
</script>
<style lang="scss" scoped>

.card{
    box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.438);
    padding: 20px 75px;
    .author{
        padding: 0 10px;
        border-bottom: 1px solid black;
        h2{
            font-weight: 600;
        }
    }
    .date{
        font-size: 0.8rem;
    }
}
</style>