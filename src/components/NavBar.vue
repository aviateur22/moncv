<template> 
 <!--animation -->
    <div class="animation">
        <BackgroundAnimation @updateTitle="this.updateTitle" />
    </div>  
    <div :class="{'header__navigation-container--hidden': !this.displayMenu}" class="container">
        
        
        <header class="header">      
                
            <nav class="header__navbar">
                <section class="header__title-container-new">
                    <span ref="darkWord" class="dark--word">{{ this.copyDarkTitle }}</span>
                    <span ref="colorWord" class="color--word"> {{ this.copyColorTitle}}</span>
                </section>
                <!-- zone de titre -->
                <!-- <section class="header__title-container"> -->
                    <!-- titre -->
                    <!-- <h1 id="title" class="header__title">DEVELOPPEUR WEB FULLSTACK JAVASCRIPT</h1> -->
                <!-- </section> -->

                <!-- zone de navigation -->
                <section  class="header__navigation-container">
                    
                    <!-- liens de navigation  -->
                    <h2><a class="header__navlink" href="#myExperience">mon parcours</a></h2>
                    <h2><a class="header__navlink" href="#techno">mes technos</a></h2>
                    <h2><a class="header__navlink" href="#project">mes projets</a></h2>
                    <h2><a class="header__navlink" href="#contact">contacts</a></h2>
                </section>  
            </nav> 
            <!-- menu mobile -->
            <section v-if="this.mobileMenuHamburger" @click="toggleMobileMenu" class="mobile">
                <div class="mobile__line"></div>
                <div class="mobile__line"></div>
                <div class="mobile__line"></div>
            </section>      
        </header>    
        <!-- <hr class="separator"> -->
    </div>
    
  <!-- overlay mobile affichant le menu -->
    <MobileNavigation v-if="this.displayMobileOverlay" @toggleMobileMenu="toggleMobileMenu"/> 
</template>

<script>
import MobileNavigation from '../components/navigation/MobileMenu.vue';
import BackgroundAnimation from './navigation/BackgroundAnimation.vue'

export default {
    
    components:{
        MobileNavigation,
        BackgroundAnimation
    },
    name:'Navigation',
    data(){
        return{
            /**affichage bouton menu hamburger */
            mobileMenuHamburger:false,

            /**Taille ecran format mobile */
            isMobileSize:null,

            /**taille de l'écran */
            windowWidth: null,

            /* position du scroll*/
            lastScrollPosition:0,

            displayMenu:true,

            /**Affichage overlay Mobile */
            displayMobileOverlay:false,

            /**Titre avec partie couleur gris */            
            darkTitle:undefined,

            /**Cpoy du titre avec partie couleur gris pour animer OPACITY*/            
            copyDarkTitle:undefined,

            /**Titre avec partie couleur bleu */            
            colorTitle:undefined,

            /**Cpoy du titre avec partie couleur bleu pour animer OPACITY*/            
            copyColorTitle:undefined
            
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
           
            /**gestion affichage du bouton hamburger */
            this.mobileMenuHamburger = !this.mobileMenuHamburger

            /**affichage overlay mennu du mobile */
             this.displayMobileOverlay= !this.displayMobileOverlay;
        },

        /**
         * Verification taille de l'ecran pour masquer le menu MOBILE
         */
        checkScreen(){
            this.windowWidth = window.innerWidth;
            if(this.windowWidth <=768){
                this.isMobileSize =true;
                this.mobileMenuHamburger=true;
                return;                
            }
            this.isMobileSize=false;
            this.mobileMenuHamburger=false;
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
        },

        /** Reception des données du titre  */
        updateTitle(data){                        
            if(this.$refs.darkWord){
                this.$refs.darkWord.style.opacity=0;
                this.$refs.colorWord.style.opacity=0;
            }
            this.colorTitle = data.colorTitle;
            this.darkTitle= data.darkTitle;            
        }
    },
    
    
    watch:{

        /**Mise a jour du titre */
        darkTitle: function (){            
             setTimeout(()=>{
                    this.copyColorTitle = this.colorTitle;
                    this.copyDarkTitle = this.darkTitle;                
                    this.$refs.darkWord.style.opacity =1;
                    this.$refs.colorWord.style.opacity =1;
                },500)
            }       
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
        }

        .header__navigation-container{
            display: none !important;
        }

        .header__title{                
        font-size: var(--text_xxl) !important;    
        }

        .mobile {
            display: flex !important;
            position: absolute !important ;
            top: 15px !important;
            right: 0px !important
        }
    }

    .container{       
        margin: 0px auto;   
        position: sticky;
        top:0px;
        transition: all var(--time1) ease;
        z-index: 6;
        padding-bottom: 35px;
        /* background-image: url('../assets/images/html.png'), url("../assets/images/css.png"),url("../assets/images/javascript.png") !important;
        background-position: 10%, center, 90%;
        background-repeat: no-repeat; */
        background-size:90px;
        background: linear-gradient(90deg, rgba(2,0,36,0.5) 0%, rgba(77,77,83,0.2) 57%, rgba(90,90,91,0.3) 100%);
        
    }

    /* gestion reduction height du container */
    .animation{
        position: absolute;
        top: 0px;
        bottom: 0px;
        width: 100%;
    }
    
    .header{
        position: relative;
    }

    .header__navbar{
        display: flex;
        flex-direction: column;
    }

    .header__title-container-new{
        max-width: 100%;
        text-align: center;        
        font-size: var(--text_xxxxl);        
        text-transform: uppercase;     
        margin-top: 20px;  

    }

    .color--word{
        color:var(--title_color);
        font-weight: 900;
        transition: all var(--time1) ease-in;

    }

    .dark--word{
        font-weight: 900;
        text-shadow: 0px 0px 1px  black;
        color: rgb(160, 160, 160);
        margin-right: 10px;
        transition: all var(--time1) ease-in;
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
        width: 100%;
        padding: 25px 15px;
    }   

    .header__navigation-container{      
        display: flex;
        align-items: center;
        justify-content: space-between;
        height: 120px;        
        transition: all var(--time1) ease-in;
        padding: 15px 100px;
    }

    /**Masquer le menu au scroll */
    .header__navigation-container--hidden{
         transform: translate3d(0, -70%, 0);
    }

    .header_navlink-container{
        display: flex;
        justify-content: space-between;
        align-items: center;   
        width: 100%;    
               
    }

    .header__navlink{    
        text-align: center;    
        text-transform: uppercase;
        text-decoration: none;
        font-weight: bold;
        color: white;
        font-size: var(--text_xl);
        cursor: pointer;
        transition: all var(--time1) ease-in-out;
        transform: translateY(70px);      
        display: inline-block;
        margin: 0px 20px;
        text-shadow: 1px 1px 2px rgb(0, 0, 0), 0 0 1em rgb(189, 189, 189), 0 0 0.2em rgb(168, 168, 168);
        
    }

    .header__navlink:hover{
        text-shadow: 0px 0px 1px black;

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

    .separator{
        border-top: 0.1px solid gray;
        max-width: 1200px;
        margin: 0px auto;
        transform: translateY(30px);
    }

    

</style>