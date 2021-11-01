<template>
  <div :class="{'show': this.show}" id="myExperience" class="container">
      <h2 class="title">mon parcours</h2>

      <section v-for="(experience,id) in this.experiences" :key="id" class="article__section">
          <div class="experience__container">
              <Experience :experience="experience"/>
          </div>          
      </section>

  </div>
</template>

<script>
import Experience from './professionnalExperience/Experience.vue'
export default {
    name:'ProfessionnalExperience',    
    components:{
        Experience
    },    
   
    mounted(){
        window.addEventListener('scroll', this.onScroll)
    },
    props:['experiences'],
    data(){
        return{           
            show : false,
        }
    },
    methods:{

        /**Gestion du défilement de la souris */
        onScroll(){
             // Position du scroll
            const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop

            // Affichage composant = 50px
            if (currentScrollPosition > 50) {
                this.show = true;
            
            }
            this.lastScrollPosition = currentScrollPosition;        

        }
    },
    

}
</script>

<style scoped>

    .container{
        max-width: 768px;
        margin: 0px auto;
        transition: all var(--time2) cubic-bezier(0.39, 0.575, 0.565, 1);
        opacity: 0;

    }

    
    .show{
        opacity: 1 !important; 
        transform: translate3d(0, -10px, 0) !important;
    }

    .title{
        text-transform: uppercase;
        font-weight: var(--text-bold);
        font-size: var(--text_xxl);
        color: var(--title_color);
        padding: 25px 0px;
        text-align: center  ;
        
    }    

    


</style>