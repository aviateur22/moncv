<template>
  <div id="project" class="container">
      <h2 class="title">projets</h2>

      <div class="project-container">
           <ProjectButton ref="projects" v-for="(project,id) in projects" :project="project" @reset-color="resetColor" @display-project="displayProject"  :key="id">  
              
            </ProjectButton>
      </div>

    <transition name="fade">
        <div ref="projectDisplay"  v-if="this.display" class="project-display">
            <ProjectDisplay :project="this.project"/>            
        </div>
    </transition>
   


  </div>
</template>

<script>
import ProjectButton from './project/ProjectButton.vue';
import ProjectDisplay from './project/ProjectDisplay.vue'
export default {
    name:'Project',
    components:{
        ProjectButton,
        ProjectDisplay
    },
    data(){
        return{            
            projects:[
                    {
                        id:0,
                        date:'2015',
                        name:"easylux",
                        technos:['C#','microsoft office'],
                        imgs:[
                            {
                                id:1,
                                url: 'easylux1-1.png',
                                alt:'premiere photo de easylux v1' 
                                },
                               {
                                   id:2,
                                   url: 'easylux1-2.png',
                                   alt:'seconde photo de easylux v1' 
                               }
                        ],
                        comments:[
                            'études problématiques dans notre travail',
                            'proposition et conception d\'un logiciel sur mesure'
                        ]
                    },
                    {
                        id:1,
                        date:'2018',
                        name:"easylux v2",
                        technos:['C# WPF' ,'requète API','sqlite'],
                        imgs:[
                                {
                                    id:1,
                                    url: 'easylux2-1.png',
                                    alt:'premiere photo de easylux v2' 
                                },
                               {
                                   id:2,
                                   url: 'easylux2-1.png',
                                   alt:'seconde photo de easylux v2' 
                               }
                            ],
                        comments:['enquête sur les besoins d\'amélioration','etablissement cahier des charges','wireframe sur figma','integration de Bigmap']
                    },
                    {
                        id:2,
                        date:'2016',
                        name:"notam manager v1",
                        technos:[ 'C#','microsoft office','requète API'],
                        imgs:[
                                {
                                    id:1,
                                    url: 'notam1-1.png',
                                    alt:'premiere photo de notam manager v1' 
                                },
                                {
                                    id:2,
                                   url: 'notam1-2.png',
                                   alt:'seconde photo de notam manager v1' 
                                }
                            ],
                        comments:['proposition logiciel pour suivre les notams d\'un aéroport','utilisation de la librairie GMAP',]
                    },
                    {
                        id:3,
                        date:'2020',
                        name:"notam manager v2",
                        technos:['Google Apps Script','javascript','requète API'],
                        imgs:[
                                {
                                    id:1,
                                    url: 'notam2-1.png',
                                    alt:'premiere photo de notam manager v2' 
                                },
                                {
                                    id:2,
                                   url: 'notam2-2.png',
                                   alt:'seconde photo de notam manager v2' 
                                }
                            ],
                        comments:['proposition d\'une évolution suite a la disparaition de m.office','enquête sur les besoins','etablissement cahier des charges','wireframe et prototyping sur figma','connexion a google drive','gestion du responsive'],
                    }
                ],
            display:false,
            project:null,
            path:'../assets/images/',
            projectIdBackup:undefined,
            
            previousElementClick:null

        }
    },
    methods:{

        /**
         * Affichage du projet en détail
         */
        displayProject(project){

           
            console.log(project)
            if(project.id===this.projectIdBackup){
               
                this.display=false;
                this.projectIdBackup=undefined
                return;
            }
            
            
            this.display=true;
            this.project=project;
            this.projectIdBackup=project.id;

            //Effet de passage d'un projet a l'autre
            if(this.$refs.projectDisplay){
                this.$refs.projectDisplay.style.opacity = 1;
                setTimeout(()=>{
                    this.$refs.projectDisplay.style.opacity = 1;
                },300)
            }
        },

        /**
         * Reset de la couleur des boutons projets
         */
        resetColor(element){
            if(this.previousElementClick && element != this.previousElementClick){

                this.previousElementClick.style.backgroundColor = 'transparent'
            }
            
            this.previousElementClick = element

        },

        /**
         * effet de masquage a l'affichage d'un nouv. projet 
         */
        hideOnClick(){


        }

       
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
    }

    .project-container{
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-wrap: wrap;
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