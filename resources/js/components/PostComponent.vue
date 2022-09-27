<template>
    <div class="container-lg">
        {{ post.description }}
    </div>
</template>

<script>
    export default {
        props:{
            post : Object,
        }
    }
</script>
