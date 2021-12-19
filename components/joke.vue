<template>
     <nuxt-link :to="'jokes/'+id">
        <div >
            <p class="joke">{{joke}}</p>
        </div>
    </nuxt-link>
</template>

<script>
    export default {
        props:["joke","id"]
    }
</script>

<style  scoped>
   .joke{
       padding: 1rem;
       border: 1px dotted #ccc;
       margin: 1rem 0;
   }
</style>