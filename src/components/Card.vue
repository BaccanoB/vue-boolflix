<template>
    <div class="card">
        <div class="info_container">
            <p><span>Titolo:</span>"{{ result.title||result.name }}"</p>
            <p><span>Titolo originale:</span>"{{ result.original_title||result.original_name }}"</p>
            <img class="flag" v-if="result.original_language == 'it'" src="../assets/it.png" alt="flag">
            <img class="flag" v-else-if="result.original_language == 'en'" src="../assets/en.png" alt="flag">
            <p v-else >Lingua: {{ result.original_language }}</p>
            <span class="star"><i :class="(star <= result.vote_average)? 'fas':'far'"
            v-for="star in 5" :key="star" class="fa-star"></i></span>
            <p class="overview" v-if="result.overview ==''">No Description Available</p>
            <p class="overview" v-else>{{ result.overview }}</p>
        </div>
        <div class="poster_container">
                <img class="null_img poster" v-if="result.poster_path == null" src="../assets/notImage.jpg" alt="img">
            <img class="poster" v-else :src="'https://image.tmdb.org/t/p/'+ '/w342/'+ result.poster_path" alt="img">
        </div>
    </div>
</template>

<script>
export default {
    name:'Card',
    props: {
        "result":Object
    }
}
</script>

<style lang="scss" scoped>

    @import '../style/variables';
    @import '../style/mixins';

    .card {
        width: 342px;
        height: 513px;
        margin: 40px 10px;
        box-shadow: 3px 3px 3px   rgba(180, 177, 177, 0.9);
        overflow: hidden;
        cursor: $pointer;

        .info_container {
            display: $none;
            height: 100%;
            width: 100%;
            padding: 20px;
            background-color: rgb(36, 34, 34);
            color: $color_text;

            span {
                color: $netflix_red;
                font-size: 25px;
                text-transform: uppercase;
            }

            p {
                font-size: 20px;
                margin: 10px 0;
            }

            .star {
                display: block;
                margin-bottom: 5px;
            }

            .flag {
                width: 50px;
                margin: 20px 0;
            }

            .fa-star {
                color: $netflix_red;
            }

            .overview {
                font-size: 15px;
            }
        }

        .poster_container {
            height: 100%;

            img {
                height: 100%;
            }

            
            .null_img {
                width: 100%;
                height: 100%;
            }
        }
    }
    .card:hover {
        box-shadow:$none;

        .info_container {
            display: block;
            transition: 3s;
        }
        .poster_container {
            display: $none;
        }
    }

</style>