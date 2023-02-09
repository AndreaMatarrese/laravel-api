<template>
    <div>
        <h1 class="text-center">Frontoffice in Vue</h1>
        <div class="row row-cols-3 container m-auto">
            <div v-for="post in arrPosts" :key="post.id" class="col">
                <div class="card h-100 index">
                    <img :src="post.image" class="img-fluid rounded-start" :alt="post.title">
                    <div class="card-body">
                        <h5 class="card-title">{{post.title}}</h5>
                        <p class="type text-uppercase">{{post.excerpt}}</p>
                        <a :href="'/posts/' + post.slug" class="btn btn-primary">Leggi</a>
                    </div>
                </div>
            </div>
        </div>
    </div>

</template>

<script>

export default {
    name: 'App',
    data() {
        return {
            arrPosts: [],
        }
    },
    created() {
        axios.get('/api/posts')
            .then(response => this.arrPosts = response.data.results)

    },

}

</script>


<style lang="scss">
@import '~bootstrap/scss/bootstrap';

</style>
