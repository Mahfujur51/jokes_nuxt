<template>
    <div>
        <h1>JOke</h1>
        <SearchJokes
            v-on:search-text="searchText"

        />
     
       <joke
            v-for="joke in jokes"
            :key="joke.id"
            :joke="joke.joke"
            :id="joke.id"
       />
    </div>
</template>

<script>
    import axios from "axios"
    export default {
        data() {
            return {
                jokes:[]
            };
        },
        async created() {
            const config={
                headers:{
                    Accept:"application/json"
                }
            };
            try {
                const res = await axios.get("https://icanhazdadjoke.com/search",config);
                // console.log(res.data.results)
                this.jokes=res.data.results
            } catch (error) {
                
            }
        },
        methods: {
            async searchText(text){    
            const config={
                headers:{
                    Accept:"application/json"
                }
            };
             try {
                const res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`,config);
                // console.log(res.data.results)
                this.jokes=res.data.results
            } catch (error) {
                
            }
            }
        },
    }
</script>

<style scoped>

</style>