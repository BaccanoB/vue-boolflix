<template>
  <div></div>
</template>

<script>
import axios from 'axios';
export default {
    name:'Main',
    created: function(){
        axios
           .get('https://api.themoviedb.org/3/search/movie',{
               params:{
                   api_key: '838b4a196c57a8cffba225213ba6f953',
                   query: String,
                   language: 'it-IT'
                }
            })
            .then(
                (res) =>{
                    console.log(res);
                }
            )
    }
}

</script>

<style>

</style>