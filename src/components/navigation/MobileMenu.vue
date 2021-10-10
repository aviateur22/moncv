<template>
    <div class="container">
        <div class="mobile-menu">
            <!-- menu close -->        
            <div @click="closeMenuOverlay" class="close-btn">
                <div class="close-btn__line1"></div>            
                <div class="close-btn__line2"></div>
            </div>    

            <!-- zone de navigation -->
            <section  class="navigation">                
                <!-- liens de navigation  -->
                <h2 @click="closeMenuOverlay"><a  class="navigation__navlink" href="#myExperience">mon parcours</a></h2>
                <h2 @click="closeMenuOverlay"><a class="navigation__navlink" href="#techno">mes technos</a></h2>
                <h2 @click="closeMenuOverlay"><a class="navigation__navlink" href="#project">mes projets</a></h2>
                <h2 @click="closeMenuOverlay"><a class="navigation__navlink" href="#contact">contacts</a></h2>
            </section>          
        </div>   

    </div>
  
</template>

<script>
export default {
    name:'MobileNavigation',
    data(){
        return{
            
        }
    },   
    methods:{
        closeMenuOverlay(){
            // renvoie false pour l'affichage de l'overlay
            this.$emit('toggleMobileMenu', true)
        }
    }

}
</script>

<style scoped>

    .display-mobile-menu{
        display: block !important;
    }
    .mobile-menu{
        display: block;
        position: fixed;
        left: 0px;
        top:0px;
        bottom: 0px;
        right: 0px;
        background-color: rgba(0, 0, 0, 0.7);
        z-index: 2;
    }


    .close-btn{
        margin: 25px;
        position: absolute;        
        cursor: pointer;        
        right: 0px;        
        top: 0px;
        overflow: hidden;
        padding:20px 0 0;
        transform: translate(-50%, -50%);
        transition: all 0.2s ease-in;
        width: 20px;

    }

    .close-btn::before,
    .close-btn::after {
        background-color: white;
        content: '';
        display: block;
        height: 2px;
        left: 0;
        position: absolute;
        transform-origin: center left;
        transition: all 0.2s ease-in;
        width: 50px;
        z-index: -1;
    }

    .close-btn::before {
    top: 0;
    transform: rotate(45deg);
    }

    .close-btn::after {
    bottom: 1;
    transform: rotate(-45deg);
    }

    .close-btn:hover::after,
    .close-btn:hover::before
    {
        height: 2.5px;

    }

    .navigation{
        height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-around;
    }

    .navigation__navlink{
        color:white;
        font-weight: 600px;
        text-transform: uppercase;
    }
</style>