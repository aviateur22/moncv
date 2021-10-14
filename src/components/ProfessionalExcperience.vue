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
    data(){
        return{
            experiences:[
                {
                    title:"reconversion professionnelle",
                    date:"aujourd'hui à 2021",
                    subTitle:"",
                    items:[
                      'HTML/CSS/Javascript',
'                      React & NodeJS',
                      'modélisation et implémentation de base de données',
                      'Gestion de projet avec la méthodologie AGILE',
                      'Déploiement sur serveur',
                      'réalisation complète d’une application WEB  ',
                    ]
                },
                {
                    title:"autodidacte",
                    date:"2021 à 2013",
                    subTitle:"Pationné par le développement WEB et logiciel:",
                    items:[
                        'Apprentissage de diffrents languages de programmation',
                        'Apprentissage de diffrents languages de programmation',
                        'Création d\'applications personnelles',
                        'Test de wireframe et prototype sur figma',
                        'ébauche de projet pour la famille',
                        'développement d\'application pour mon travail'
                    ]

                }
            ],
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