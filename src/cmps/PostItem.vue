<template>
    <div class="row col-12 post mb-5">
        <div class="col-4 col-sm-4 text-center">
            <img alt="" class="img-fluid" 
            v-if="post.post_featured_image !== ''" 
            :src= "'http://localhost/restapi/public/assets/uploads/' + post.post_featured_image "> 
            <img v-else :src="imgPlaceholder" alt="">       
        </div>
        <div class="col-8 col-sm-8">
            <h3>{{post.post_title}}</h3>
            <p>{{post.post_description}}</p>
        </div>
        <div class="col-12 mt-3 pl-3">
            <router-link class="btn btn-outline-success mr-2" :to="'/post/' + post.post_id"> View </router-link>
            <button class="btn btn-outline-primary" @click="$emit('edit', post.post_id, index)">Edit</button>
            <button class="btn btn-outline-danger float-right" @click="$emit('delete', post.post_id, index)">Delete</button>
        </div>
        <div class="col-12">
            <hr>
        </div>
    </div>
</template>

<script>

    export default {

        props: ['post', 'index', 'imgPlaceholder']
        
    } 

</script>

<style>

</style>