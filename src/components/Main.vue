<template>
    <section>
        <div id="container">
            <div v-for="movie in movies" :key="movie.id">
                <p>{{ movie.title }}</p>
                <p>{{ movie.original_title }}</p>
                <img v-if="movie.original_language == 'it'" src="../assets/it.png" alt="">
                <img v-else-if="movie.original_language == 'en'" src="../assets/en.png" alt="">
                <p v-else >{{ movie.original_language }}</p>
                <p>{{ movie.vote_average }}</p>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name:'Main',
    props: ['movies']
}

</script>

<style lang="scss" scoped>
    section {
        width: 100%;
        height: calc(100% - 80px);
        background-color: #303030;

        #container {
            width: 80%;
            margin: 0 auto;
            height: 100%;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: center;

            & > div {
                width: calc(100% / 6);
                height: 200px;
                margin: 10px;
                text-align: center;

                img {
                    width: 20px;
                }
            }
        }
    }
</style>