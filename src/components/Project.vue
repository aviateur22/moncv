<template>
  <div :class="{'show':this.show}" id="project" class="container">
      <h2 class="title">projets</h2>
      

        <div class="project-container">
            <!-- info bulle -->
            <div class="profil__bubble">
                <Bubble :data="bubbleInformation"/>
            </div>           
            <!-- Affichage des projets -->
            <ProjectDisplay :project="project" v-for="(project,id) in projects" :key="id"/>  
        </div>
  </div>
</template>

<script>
import ProjectDisplay from './project/ProjectDisplay.vue';
import Bubble from './bubble/InformationBubble.vue'
export default {
    name:'Project',
    props:['projects'],
    components:{
        ProjectDisplay,
        Bubble
    },
     mounted(){
        window.addEventListener('scroll', this.onScroll);          
    },
    data(){
        return{                        

            bubbleInformation:{
                title:"Astuce",
                text:"Cliquer sur un projet pour avoir plus de détail"
            },
            show:false

        }
    },
    methods:{

        /**Gestion du défilement de la souris */
        onScroll(){
             // Position du scroll
            const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop

            // Affichage composant = 50px
            if (currentScrollPosition > 1250) {
                this.show = true;
            
            }
            this.lastScrollPosition = currentScrollPosition;        

        }
    },
    watch:{


    }
    

    

}
</script>

<style scoped>
    @media(max-width: 768px){

        .project-container{
            flex-direction: column !important;            
        }

        .project{
            margin: 15px 0px;
        }

        .presentation__img-container{
            max-width: 320px !important;
        }

         .presentation__btn{
            top: calc(110% - 25px) !important;
        }
    }

    @media(max-width:1440px){
        .project-container{
            max-width: 800px !important;      
            margin: 0px auto;      
        }
    }
    .container{
        max-width: 1600px;
        margin: 35px auto;    
        transition: all var(--time2) cubic-bezier(0.39, 0.575, 0.565, 1);
        opacity: 0;    
        
    }

      .show{
        opacity: 1 !important; 
        transform: translate3d(0, -10px, 0) !important;
    }

    .project-container{
        position: relative;
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-wrap: wrap;
    }

     .profil__bubble{
        position:absolute;
        top: 0px;
        right:0px;   
        transform:translateY(-100px);
        z-index: 2;
    }

    .title{
        text-transform: uppercase;
        font-weight: var(--text-bold);
        font-size: var(--text_xxl);
        color: var(--title_color);
        padding: 25px 0px;
        text-align: center;
    }

   

    /* Presentation du projet */

    .project-display{
        transition: all var(--time1) ease-in;
    }

    .fade-enter-active {
        animation: bounce-in .5s;
    }
    .fade-leave-active {
        animation: bounce-in .5s reverse;
    }
    @keyframes bounce-in {
        0% {
            transform: scale(0);
        }
        50% {
            transform: scale(1.5);
        }
        100% {
            transform: scale(1);
        }
    }

    .project-display{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;  
        position: relative;
    }

    


    
</style>