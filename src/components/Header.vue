<template>
  <section>
      <div id="logo">
          <img src="../assets/logo.png" alt="logo">
      </div>
      <div id="search_bar">
          <input v-model="text" type="text">
          <button @click="searchMovie">Cerca</button>
      </div>
  </section>
</template>

<script>
export default {
    name:'Header',
    data() {
        return {
            text: ''
        }
    },
    methods: {
        searchMovie() {
            this.$emit('userResearch',this.text)
        }
    }
}
</script>

<style lang="scss" scoped>
    section {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 5px 10px;
        width: 100%;
        height: 80px;
        background-color: black;

        div {
            display: flex;
            align-items: center;
            width: 50%;
            height: 100%;
        }
        #logo {
            img{
                width: 20%;
            }
        }
        #search_bar {
            justify-content: flex-end;
            input {
                width: 60%;
                height: 30px;
                margin-right: 20px;
            }
            button {
                padding: 10px;
                text-transform: uppercase;
                font-weight: bolder;
                color: white;
                border: 1px solid #DC1A28;
                border-radius: 5px;
                background-color: #DC1A28;
            }
        }
    }

</style>