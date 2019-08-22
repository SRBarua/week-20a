<template>
    <div>
        <div>
            <div>
                <form @submit.prevent="doSearch">
                    <input v-model="query" type="text" placeholder="GIF Search" />
                    <button type="submit" class="btn btn-primary">Go</button>
                </form>
            </div>
            <div>
                <img v-for="result in results" :src="result.images.fixed_height.url" />
            </div>
        </div>
    </div>

</template>
<script>
    import axios from 'axios'
    export default {
        data() {
            return {
                apiKey: 'EXUoxgZA4Ksq3OvB9o75z0mHlrQqSUse',
                query: '',
                results: [],
            }
        },

        methods: {
            doSearch() {
                axios.get( 'https://api.giphy.com/v1/gifs/search?api_key=' + this.apiKey + '&q=' + this.query)
                    .then ((response) => {
                        this.results = response.data.data;    
                    })
            }
    }
}
</script>


<style lang="scss">
</style>
