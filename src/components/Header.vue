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
            <img src="../assets/iconaUtente.jpg" alt="icona_utente">
            <div id="dropdown_container">
                <i class="fas fa-caret-down"></i>
                <div id="dropdown">
                    <div id="users">
                        <div>
                            <img src="../assets/lucy_logo.png" alt="img">
                            <p>Valerio</p> 
                        </div>
                        <div>
                            <img src="../assets/bojack_icon.jpg" alt="img">
                            <p>Tommaso</p>
                        </div>
                    </div>
                    <p>Gestisci i profili</p>
                    <hr>    
                    <ul>
                        <li>Account</li>
                        <li>Centro Assistenza</li>
                        <li>Esci da Beatflix</li>
                    </ul>
                </div>
            </div>
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

    @import '../style/variables';
    @import '../style/mixins';

    section {
        position: fixed;
        top: 0;
        @include flex;
        justify-content: space-between;
        padding: 5px 10px;
        width: 100%;
        height: 80px;
        background-color: black;
        z-index: 2;

        nav {
            width: 70%;
            margin-left: 30px;
            @include flex;
            color: $color_text;

            ul {
                list-style: $none;

                li {
                    display: inline-block;
                    margin-right: 20px;
                    font-size: 18px;
                    transition: $scale;
                }
                li:hover {
                    color: $color_hover;
                    cursor:$pointer;
                }
            }
        }

        div {
            @include flex;
            width: 50%;
            height: 100%;
        }

        #logo {
            img {
                width: 20%;
            }
        }

        #search_bar {
            position: relative;
            justify-content: flex-end;
            color: $color_text;

            i {
                font-size: 18px;
                margin: 0 10px;
            }
            i:hover {
                cursor:$pointer;
            }

            #dropdown_container {
                width: 20px;
                margin-right: 10px;

                #dropdown {
                    display: $none;
                    position: absolute;
                    right: 450px;
                    top: 60px;
                    width: 150px;
                    height: 220px;
                    padding: 15px;
                    background-color: rgba(0, 0, 0, 0.7);

                    & > p {
                        margin: 15px 0;
                        cursor:$pointer;
                        transition: $scale;
                    }
                    & > p:hover {
                        color: $color_hover;
                    }

                    & > ul {
                        list-style: $none;

                        li {
                            margin: 5px 0; 
                            cursor:$pointer;
                            transition: $scale;                                            
                        }
                        li:hover {
                            color: $color_hover;
                        }
                    }

                    #users {
                        display: flex;
                        flex-direction: column;
                        align-items: flex-start;
                        height: 40%;
                        & > div {
                            padding: 5px 0;
                            & > img {
                                width: 30px;
                                border-radius: 5px;
                            }
                            & > p {
                                margin-left: 5px;
                                cursor:$pointer;
                                transition: $scale;
                            }
                            & > p:hover {
                                color: $color_hover;
                            }
                        }
                    }
                }
            }
            #dropdown_container:hover #dropdown {
                display: block;
            }
        
            & > img {
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
                border: 2px solid $netflix_red;
                font-weight: bolder;
                font-size: 15px;
            }
            button {
                padding: 10px;
                text-transform: uppercase;
                font-weight: bolder;
                cursor:$pointer;
                color: $color_text;
                border: 1px solid $netflix_red;
                border-radius: 5px;
                background-color: $netflix_red;
            }
            button:hover {
                transform: scale(1.1);
            }
        }
    }

</style>