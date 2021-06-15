<template>
    <section>
        <div id="bg_opacity">
            <div id="container">
                <div v-for="result in search" :key="result.id">
                    <p>{{ result.title||result.name }}</p>
                    <p>{{ result.original_title||result.original_name }}</p>
                    <img v-if="result.original_language == 'it'" src="../assets/it.png" alt="">
                    <img v-else-if="result.original_language == 'en'" src="../assets/en.png" alt="">
                    <p v-else >{{ result.original_language }}</p>
                    <p>{{ result.vote_average }}</p>
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
                    margin: 10px;
                    text-align: center;

                    img {
                        width: 20px;
                    }
                }
            }


        }
    }
</style>