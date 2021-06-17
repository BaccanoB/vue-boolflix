<template>
    <section>
        <div id="opacity">
            <div id="container">
                <Card v-for="result in search" :key="result.id" :result="result"/>
            </div>
        </div>
    </section>
</template>

<script>
import Card from "./Card.vue"
export default {
    name:'Main',
    components:{
        Card
    },
    props: ['search']
}
</script>

<style lang="scss" scoped>

    @import '../style/variables';
    @import '../style/mixins';

    section {
        width: 100%;
        min-height: 100vh;
        margin-top: 80px;
        background-image: url(../assets/jumbotron.png);
        background-repeat:repeat;

        #opacity {
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
        }

        #container {
            width: 90%;
            margin: 0 auto;
            @include flex;
            flex-wrap: wrap;
            justify-content: center;
        }   
    }
</style>