<template>
    <section>
        <div id="opacity">
            <div id="container">
                <div class="card" v-for="result in search" :key="result.id">
                    <div class="info_container">
                        <p><span>Titolo:</span> {{ result.title||result.name }}</p>
                        <p><span>Titolo originale:</span> {{ result.original_title||result.original_name }}</p>
                        <img class="flag" v-if="result.original_language == 'it'" src="../assets/it.png" alt="flag">
                        <img class="flag" v-else-if="result.original_language == 'en'" src="../assets/en.png" alt="flag">
                        <p v-else >Lingua: {{ result.original_language }}</p>
                        <span class="star"><i :class="(star <= result.vote_average)? 'fas':'far'"
                        v-for="(star,index) in 5" :key="index" class="fa-star"></i></span>
                        <p class="overview" v-if="result.overview ==''">No Description Available</p>
                        <p class="overview" v-else>{{ result.overview }}</p>
                    </div>
                    <div class="poster_container">
                         <img class="null_img poster" v-if="result.poster_path == null" src="../assets/notImage.jpg" alt="img">
                        <img class="poster" v-else :src="'https://image.tmdb.org/t/p/'+ '/w185/'+ result.poster_path" alt="img">
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
        min-height: 100vh;
        margin-top: 80px;
        background-image: url(../assets/jumbotron.jpg);
        background-repeat:repeat;

        #opacity {
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
        }

        #container {
            width: 90%;
            margin: 0 auto;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: center;

            .card {
                width: 185px;
                height: 250px;
                margin: 40px 10px;
                box-shadow: 3px 3px 3px   rgba(241, 237, 237, 0.9);
                overflow: hidden;

                .info_container {
                    display: none;
                    height: 100%;
                    width: 100%;
                    padding: 3px 5px;
                    background-color: rgb(36, 34, 34);
                    color: white;

                    span {
                        color: #DC1A28;
                        font-size: 15px;
                    }

                    p {
                        font-size: 13px;
                        margin: 2px 0;

                    }

                    .overview {
                        font-size: 45%;
                    }

                    .star {
                        display: block;
                        margin-bottom: 5px;
                    }

                    .flag {
                        width: 20px;
                        margin: 2px 0;
                    }

                    .fa-star{
                        color: #DC1A28;
                    }
                }

                .poster_container{
                    height: 100%;

                    img{
                        width: 100%;
                        height: 100%;
                    }
                    
                    .null_img {
                        width: 100%;
                        height: 100%;
                    }
                }
            }
            .card:hover {
                .info_container {
                    display: block;
                    transition: 3s;
                }
                .poster_container {
                    display: none;
                }
            }
        }


        
    }
</style>