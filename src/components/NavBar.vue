<template>
<div :class="{'header__navigation-container--hidden': !this.displayMenu}" class="container">
    <header class="header">      
        <nav class="header__navbar">
            <!-- zone de titre -->
            <section class="header__title-container">
                <!-- titre -->
                <h1 id="title" class="header__title">DEVELOPPEUR WEB FULLSTACK JAVASCRIPT</h1>
                <!-- <TitleAnimation :letter="letter" v-for="(letter,id ) in  this.titleArray[this.wordIndex][this.letterIndex]" :key="id">

                </TitleAnimation> -->
            </section>

            <!-- zone de navigation -->
            <section  class="header__navigation-container">
                
                <!-- liens de navigation  -->
                <h2><a class="header__navlink" href="#myExperience">mon parcours</a></h2>
                <h2><a class="header__navlink" href="#techno">mes technos</a></h2>
                <h2><a class="header__navlink" href="#project">mes projets</a></h2>
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
        MobileNavigation,
    },
    name:'Navigation',
    data(){
        return{
            mobileMenu:false,
            isMobileSize:null,
            windowWidth: null,
            lastScrollPosition:0,
            displayMenu:true
            
        }
    },
    mounted(){
        window.addEventListener('resize', this.checkScreen);
        window.addEventListener('scroll', this.onScroll)
    },
    beforeUnmount(){
        /** getion du menu responsive*/
        window.removeEventListener('resize', this.checkScreen);
        /** getion du scroll pour le menu*/
        window.removeEventListener('scroll', this.onScroll);


    },
    created(){

       
        //Verification au chargement de la position du scroll et taille de l'écran
        this.checkScreen();
        this.navHeight();

    },
    methods:{

        /**action de bouton menu hanburger */
        toggleMobileMenu(){
            this.mobileMenu = !this.mobileMenu
        },

        updateMobileMenudata(data){
            this.mobileMenu = data
        },        

        /**
         * Verification taille de l'ecran pour masquer le menu MOBILE
         */
        checkScreen(){
            this.windowWidth = window.innerWidth;
            if(this.windowWidth <=768){
                this.isMobileSize =true;
                return;                
            }
            this.isMobileSize=false;
            this.mobileMenu=false;
        },
        onScroll(){  
            // Position du scroll
            const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop

            // pour le mobile
            if (currentScrollPosition < 0) {
            return
            }

            //offset pour activer la disparaition du menu
            if (Math.abs(currentScrollPosition - this.lastScrollPosition) < 60) {
                return
            }            
            this.displayMenu = currentScrollPosition < this.lastScrollPosition;
            this.lastScrollPosition = currentScrollPosition;        
        },
        navHeight(){
            if (document.body.scrollTop > 80 || document.documentElement.scrollTop > 80) {                
                // console.log('scroll > 80px');
               this.height="height:100px"
               //this.setNavHeight("height:100px")
            }
            else
            {
              //console.log('scroll < 80px');
             //this.setNavHeight("height:213px")
               this.height="height:213px"
            }
        }
    },    
    watch:{
       
    },
    computed:{
        setNavHeight(){
            console.log(this.height);
            return this.height
        }
     
    }
}
</script>

<style scoped>

    @media(max-width: 768px){
        .header{
            position: relative;
            min-height: 80px;
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
        margin: 0px auto;   
        position: sticky;
        top:0px;
        background-color: white;
        transition: all var(--time1) ease;
        z-index: 6;
        padding-bottom: 35px;
    }

    /* gestion reduction height du container */

    

    .header__navbar{
        display: flex;
        flex-direction: column;
    }

    .header__title-container{
        display: flex;
        justify-content: flex-start;

    }

    .header__title{        
        font-weight: var(--text-bolder);
        font-size: var(--text_xxxl);        
        padding: 15px 0px;
        text-shadow: 1px 1px 2px black, 0 0 1em black, 0 0 0.2em black;
        color: white;
        background-color: white;
        width: 100%;
        padding: 25px 15px;
        background-color: white;

    }   

    .header__navigation-container{      
        display: flex;
        align-items: center;
        justify-content: space-between;
        height: 90px;
        background-image: url('../assets/images/html.png'), url("../assets/images/css.png"),url("../assets/images/javascript.png") !important;
        background-position: 10%, center, 90%;
        background-repeat: no-repeat;
        background-size:contain;
        background-color:white;
        transition: all var(--time1) ease-in;
        padding: 15px 180px;
    }

    /**Masquer le menu au scroll */
    .header__navigation-container--hidden{
         transform: translate3d(0, -80%, 0);
    }

    .header_navlink-container{
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;        
        width: 155px;
        
    }

    .header__navlink{
        display: block;
        text-transform: uppercase;
        text-decoration: none;
        font-weight: bold;
        color: var(--menu_color);
        font-size: var(--text_xl);
        cursor: pointer;
        transition: all var(--time1) ease-in-out;
        transform: translateY(70px);
        
        
    }

    .header__navlink:hover{
        text-shadow: 1px 1px 2px black;

    }

    .mobile{
        display:none;
        flex-direction: column;
        margin: 15px;
    }

    .mobile__line{
        margin: 3px 0px;
        height: 4px;
        width: 30px;
        background-color: var(--title_color);
    }

    

</style>