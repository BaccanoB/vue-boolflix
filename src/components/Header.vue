<template>
  <section>
      <div id="logo">
          <img src="../assets/logo.png" alt="logo">
          <nav>
          <ul>
              <li>Home</li>
              <li>Serie Tv</li>
              <li>Film</li>
              <li>Nuovi e Popolari</li>
              <li>La mia Lista</li>
          </ul>
      </nav>
      </div>
      <div id="search_bar">
          <i class="fas fa-search"></i>
          <i class="fas fa-bell"></i>
          <img src="../assets/iconaUtente.jpg" alt="">
          <i class="fas fa-caret-down"></i>
          <input placeholder="Cerca Film e Serie Tv" v-model="text" type="text">
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
        position: fixed;
        top: 0;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 5px 10px;
        width: 100%;
        height: 80px;
        background-color: black;
        z-index: 2;

        nav{
            width: 70%;
            margin-left: 30px;
            display: flex;
            align-items: center;
            
            color: white;

            ul {
                list-style: none;

                li{
                    display: inline-block;
                    margin-right: 20px;
                    font-size: 18px;
                    transition: 0.3s;
                }
                li:hover {
                    color: rgb(180, 177, 177);
                    cursor: pointer;
                }
            }
        }

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
            color: white;

            i {
                font-size: 18px;
                margin: 0 10px;
            }
            i:hover {
                cursor: pointer;
            }

            & >img {
                width: 40px;
                height: 40px;
                margin-left: 20px;
                border-radius: 5px;
            }

            input {
                width: 50%;
                height: 30px;
                padding: 3px;
                margin-right: 20px;
                border-radius: 5px;
                border: 2px solid #DC1A28;
                font-weight: bolder;
                font-size: 15px;
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