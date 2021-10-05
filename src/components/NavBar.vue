<template>
<div class="container">
    <header class="header">      
        <nav class="header__navbar">
            <!-- zone de titre -->
            <section class="header__title-container">
                <!-- titre -->
                <h1 class="header__title">DEVELOPPEUR WEB FULLSTACK JAVASCRIPT</h1>
            </section>

            <!-- zone de navigation -->
            <section class="header__navigation-container">
                
                <!-- liens de navigation  -->
                 <div class="header_navlink-container">
                    <img class="header_navlink-picture" src="../assets/images/logo.png" alt="ma photo">
                    
                </div>

                <div class="header_navlink-container">
                    <img class="header_navlink-picture" src="../assets/images/html.png" alt="ma photo">
                    <h2><a class="header__navlink" href="#myExperience">mon parcours</a></h2>
                </div>
                
                <div class="header_navlink-container">
                    <img class="header_navlink-picture" src="../assets/images/javascript.png" alt="ma photo">
                    <h2><a class="header__navlink" href="#me">mes technos</a></h2>
                </div>

                <div class="header_navlink-container">
                    <img class="header_navlink-picture" src="../assets/images/css.png" alt="ma photo">
                    <h2><a class="header__navlink" href="#me">mes projets</a></h2>
                </div>                
            </section>  
        </nav> 
        <!-- menu mobile -->
        <section v-if="!this.mobileMenu" @click="toggleMobileMenu" class="mobile">
            <div class="mobile__line"></div>
            <div class="mobile__line"></div>
            <div class="mobile__line"></div>
        </section>      
    </header>  

    <!-- overlay mobile affichant le menu -->
    <MobileNavigation @updateMobileMenudata="updateMobileMenudata" v-bind:data="this.mobileMenu"/>
</div>
  
</template>

<script>
import MobileNavigation from '../components/navigation/MobileMenu.vue';

export default {
    
    components:{
        MobileNavigation
    },
    name:'Navigation',
    data(){
        return{
            mobileMenu:false,
            isMobileSize:null,
            windowWidth: null,
        }
    },
    created(){

        window.addEventListener('resize', this.checkScreen);
        this.checkScreen();

    },
    methods:{

        toggleMobileMenu(){
            this.mobileMenu = !this.mobileMenu
        },

        updateMobileMenudata(data){
            this.mobileMenu = data
        },        

        checkScreen(){
            this.windowWidth = window.innerWidth;
            if(this.windowWidth <=768){
                this.isMobileSize =true;
                return;                
            }
            this.isMobileSize=false;
            this.mobileMenu=false;
        }
        
    }

}
</script>

<style scoped>

    @media(max-width: 768px){
         .header{
             position: relative;
             min-height: 90px;
             background-image: url('../assets/images/html.png'), url("../assets/images/css.png"),url("../assets/images/javascript.png") !important;
             background-repeat: no-repeat;
             background-size: contain;
             background-position: 10% ,center,90%;
         }
        .header__navigation-container{
            display: none !important;
        }

        .mobile {
            display: flex !important;
            position: absolute;
            top: 15px;
            right: 0px;
        }
    }
    .container{
        padding: var(--padding_navbar);
        margin: 0px auto;        
    }

    .header__navbar{
        display: flex;
        flex-direction: column;
    }

    .header__title-container{
        display: flex;
        justify-content: flex-start;

    }

    .header__title{
        opacity: 1 !important;
        font-weight: var(--text-bolder);
        font-size: var(--text_xxxl);        
        padding: 15px 0px;
        text-shadow: 1px 1px 2px black, 0 0 1em black, 0 0 0.2em black;
        color: white;

    }

    .header__navigation-container{      
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .header_navlink-container{
          position: relative;
          display: flex;
          justify-content: center;
          align-items: center;
          height: 155px;
          width: 155px;
          
    }

    .header_navlink-picture{
        position: absolute;
        max-width: 100%;
        left: 0px;
        top: 0px;
        opacity: 0.1;
        z-index: -1;

    }

    .header__navlink{
        text-transform: uppercase;
        text-decoration: none;
        font-weight: bold;
        color: var(--menu_color);
        font-size: var(--text_xl);
        cursor: pointer;
        transition: all var(--time1) ease-in-out;
    }

    .header__navlink:hover{
        text-shadow: 1px 1px 2px black;

    }

    .mobile{
        display:none;
        flex-direction: column;
    }

    .mobile__line{
        margin: 3px 0px;
        height: 4px;
        width: 30px;
        background-color: var(--title_color);
    }

    

</style>