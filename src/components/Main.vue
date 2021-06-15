<template>
    <section>
        <div id="bg_opacity">
            <div id="container">
                <div v-for="result in search" :key="result.id">
                    <div class="info_container">
                        <p>{{ result.title||result.name }}</p>
                        <p>{{ result.original_title||result.original_name }}</p>
                        <img class="flag" v-if="result.original_language == 'it'" src="../assets/it.png" alt="">
                        <img class="flag" v-else-if="result.original_language == 'en'" src="../assets/en.png" alt="">
                        <p v-else >{{ result.original_language }}</p>
                        <p>{{ result.vote_average }} <i class="fas fa-star"></i></p>
                    </div>
                    <div class="poster_container">
                         <img class="null_img poster" v-if="result.poster_path == null" src="../assets/notImage.jpg" alt="img">
                        <img class="poster" v-else :src="'https://image.tmdb.org/t/p/'+ '/w154/'+ result.poster_path" alt="">
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name:'Main',
    props: ['search']
}

</script>

<style lang="scss" scoped>
    section {
        width: 100%;
        height: calc(100% - 80px);
        // background-image: url('../assets/jumbotron.jpg');
        // background-size: cover;

        #bg_opacity {
            position: relative;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.3);

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
                    height: 250px;
                    margin: 10px;
                    text-align: center;

                    .flag {
                        width: 20px;
                    }

                    .null_img {
                        width: 154px;
                        height: 200px;
                    }
                }
            }


        }
    }
</style>