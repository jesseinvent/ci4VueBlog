<template>
    <div v-if="post" class="row col-12 post mt-4 mb-5 pt-4 pb-3 bg-white from-wrapper">
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
            <router-link class="btn btn-outline-success mr-2" to="/"> All Posts </router-link>
        </div>
       
    </div>
</template>

<script>

    export default {

        data () {
          return {
            post: false,
            imagePlaceholder: 'http://via.placeholder.com/300'
          }
        },

        methods: {

          get () {

            let id = this.$route.params.id;
            this.$api.get('/blog/' + id).then(res => {
              console.log(res);
              
              this.post = res.data;

            })
            .catch(err => {
              console.log(err.response);
              
            })

          }

        },
        
        created () {
          this.get();
        }
    } 

</script>

<style>

</style>