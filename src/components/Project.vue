<template>
  <div class="container">
      <h2 class="title">projets</h2>

      <div class="project-container">
           <article @click="displayProject(id)" class="project" v-for="project,id in projects" :key="id">  
               <!-- overlay de décoration -->
               <div class="project__overlay">project{{ project.id +1}}</div>              
                <div class="project__title-border">
                    <h2 class="project__title">                    
                        <span class="project__title-regular">projet:</span> {{ project.name}}
                    </h2>
                </div>
                

                <p class="project__date">
                  <span class="project__title-regular"> début: </span>  {{ project.date }}
                </p>
            </article>
      </div>

    <div v-if="display" :bind="this.project" class="presentation">
        <h2 class="presentation__title">
            {{ this.project.name }}
        </h2>
        <div class="presentation__img-container">
            
            <section class="presentation__techno-container">
                <ul class="presentation__techno-list">
                     <div v-for="(img,id) in this.project.imgs" :key="id">
                        <img :src="this.getImg(img.url)" :alt="img.alt" class="presentation__img">    
                     </div>
                </ul>
            </section>
        </div>
        <div class="presentation__text-container">
            <section class="presentation__techno-container">
                <ul class="presentation__techno-list">
                    <li class="presentation__techno-item" v-for="techno,id in this.project.technos" :key="id">
                        {{ techno }}
                    </li>
                </ul>
            </section>
            <section class="presentation__comment-container">
                <ul class="presentation__comment-list">
                    <li class="presentation__comment-item" v-for="comment,id in this.project.comments" :key="id">
                        {{ comment }}
                    </li>
                </ul>
            </section>
        </div>
        
    </div>


  </div>
</template>

<script>
export default {
    name:'Project',
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
                                url: 'easylux1-1.png',
                                alt:'premiere photo de easylux v1' 
                                },
                               {
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
                                    url: 'easylux2-1.png',
                                    alt:'premiere photo de easylux v2' 
                                },
                               {
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
                                    url: 'notam1-1.png',
                                    alt:'premiere photo de notam manager v1' 
                                },
                                {
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
                                    url: 'notam2-1.png',
                                    alt:'premiere photo de notam manager v2' 
                                },
                                {
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
            idBackup:undefined

        }
    },
    methods:{

        /**
         * Affichage du projet
         */
        displayProject(id){
            if(id===this.idBackup){
                this.display=false;
                return;
            }
                
            this.display=true;
            this.project=this.projects[id];
            this.idBackup=id;
            

        },

        /**
         * Renvoie l'url de l'image
         */
        getImg(name){
            return require('../assets/images/'+ name)
        }
    }
    

    

}
</script>

<style scoped>
    .container{
        max-width: 1600px;
        margin: 35px auto;
    }

    .project-container{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .project{
        position: relative;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width:280px;
        cursor: pointer;
        padding: 25px;
        overflow: hidden;
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 5px;
        border-radius: 10px;
    }

    .project__overlay{
        display: flex;
        position: absolute;
        top: 0px;
        bottom: 0px;
        left: 0px;
        right: 0px;        
        background-color: rgba(99, 98, 98, 0.4);
        transition: all var(--time1) ease-in;
        color: white;
        text-transform: uppercase;
        align-items: center;
        justify-content: center;
        
    }

    /* .project__title-border{
        padding: 3px;
        transform: translateX(-500px);
        transition: all var(--time1) ease-in;
        background-color: #34568B;
        opacity: 0;
        
    } */
    .project__title{
        border: 1px solid white;
        background-color: rgba(105, 108, 112, 0.6);
        color: white;
        font-weight: var(--text-bolder);
        text-transform: uppercase;
        transform: translateX(-500px);
        transition: all var(--time1) ease-in;
        padding: 5px 30px;
        opacity: 0;
        border-radius: 5px;
        box-shadow: rgba(0, 0, 0, 0.24) 2px 3px 5px;
        text-shadow: 1px 1px 2px black, 0 0 1em rgb(70, 69, 69), 0 0 0.2em rgb(107, 107, 107);
    }

    .project__date{
         border: 1px solid white;
        background-color: #444344;  
        color: white;      
        font-weight: var(--text-bolder);
        text-transform: uppercase;
        transform: translateX(+500px);
        transition: all var(--time1) ease-in-out;
        padding: 5px 30px;
        opacity: 0;

    }
    .project:hover .project__title{
        transform: translateX(0px);
         opacity: 1;
    }

    .project:hover .project__title-border{
        transform: translateX(0px);
         opacity: 1;
    }

    .project:hover .project__date{
        transform: translateX(0px);
        transform: translatey(-5px);
        opacity: 1;
    }

    .project:hover .project__overlay{
        opacity: 0;
    }   

    .project__title-regular{    
        font-weight: 400;
        text-transform: lowercase;
        font-size: var(--text_s);
        color:  white;
        padding-right: 10px;
        
        
    }



</style>