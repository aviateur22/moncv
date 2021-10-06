<template>
  <div id="project" class="container">
      <h2 class="title">projets</h2>

      <div class="project-container">
           <article ref="projects"  @click="displayProject(id)" class="project" v-for="project,id in projects" :key="id">  
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

    <transition name="fade">
        <div v-if="display" :bind="this.project" class="presentation">
            <h2 class="presentation__title">
                {{ this.project.name }}
            </h2>
                    
            <section class="presentation__img-container">                                
                <img @click="displayInformation" ref="image" class="presentation__img" :src="this.getImg(this.project.imgs,this.imgId)" :alt="this.project.imgs[this.imgId].alt"> 
                <button class="presentation__btn presentation--left" @click="previousImg(this.project.imgs,this.imgId)">&lt;</button>
                <button class="presentation__btn" @click="nextImg(this.project.imgs,this.imgId)">&gt;</button>
                 <div ref="information" class="presentation__text-container">
                     <button @click="closedPresentation" class="presentation_text-closed">&times;</button>
                     <!-- techno utilisé -->
                    <section class="presentation__techno-container">
                        <ul class="presentation__techno-list">
                            <li class="presentation__techno-item" v-for="techno,id in this.project.technos" :key="id">
                                {{ techno }}
                            </li>
                        </ul>
                    </section>
                    <!-- role de joué -->
                    <section class="presentation__comment-container">
                        <ul class="presentation__comment-list">
                            <li class="presentation__comment-item" v-for="comment,id in this.project.comments" :key="id">
                                {{ comment }}
                            </li>
                        </ul>
                    </section>
                </div>                
            </section>
        
           
            
        </div>
    </transition>
   


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
            imgId:0

        }
    },
    methods:{

        /**
         * Affichage du projet en detail
         */
        displayProject(id){
            if(id===this.projectIdBackup){
               
                this.display=false;
                this.projectIdBackup=undefined
                return;
            }
            
            this.display=true;
            this.project=this.projects[id];
            this.projectIdBackup=id;
            

        },

        displayInformation(){
            this.$refs.information.style.transform = "translateY(-253px)"
        },

        closedPresentation(){
            this.$refs.information.style.transform = "translateY(0px)"
        },
        /**
         * Renvoie l'url de l'image utilisable par VUEJS
         */
        getImg(imgDataArray, id){

            try{
                return require('../assets/images/'+ imgDataArray[id].url);
            }
            catch(err){
                console.log('url image:' + url)
                console.log(err)
            }
            
          
        },

        /**
         * Passe à l'image suivante
         */
        async nextImg(imgDataArray, id){
            this.rightAnimationEffect();
            setTimeout(() => {  

                const count = this.imgId + 1;            

                if(count > imgDataArray.length-1){
                    
                    this.imgId = 0
                }                  
                else
                {   
                    this.imgId = count
                }

                 this.resetAnimation();

           }, 500);
        },

        /**
         * Passe a l'image précedente
         */
        async previousImg(imgDataArray){

            this.leftAnimationEffect();

            setTimeout(() => {  

                const count = this.imgId - 1; 


                if(count < 0){
                    
                    this.imgId = imgDataArray.length-1
                }                  
                else
                {   
                    this.imgId = count
                }

                this.resetAnimation();
           }, 500);
        },       

        /**
         * slide right
         */
        rightAnimationEffect(){
          this.$refs.image.style.transform = "translateX(500px)";
          this.$refs.image.style.opacity = 0;           
        },

        /**
         * slide left
         */
        leftAnimationEffect(){
          this.$refs.image.style.transform = "translateX(-500px)";
          this.$refs.image.style.opacity = 0;           
        },

        /**
         * controle du reste de l'image
         */
        resetAnimation(){
            this.startResetAnimation();

            setTimeout(() => {  
                this.finishResetAnimation();
            },200);
        },

        /**
         * remplacement de l'image
         */
        startResetAnimation(){
          this.$refs.image.style.transform = "translateX(0px)";        
         
        },

        /**
         * reset opacity
         */
        finishResetAnimation(){
            this.$refs.image.style.opacity = 1;        
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
    .container{
        max-width: 1600px;
        margin: 35px auto;
    }

    .project-container{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .title{
           text-transform: uppercase;
        font-weight: var(--text-bold);
        font-size: var(--text_xxl);
        color: var(--title_color);
        padding: 25px 0px;
        text-align: center;
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

    /* Presentation du projet */

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

    .presentation{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;  
        position: relative;    
        
        
    }

    .presentation__title{
        padding: 40px 0px;
        text-transform: uppercase;
        font-size: var(--text_xxxl);
        font-weight: var(--text-bolder);
    }

    .presentation__img-container{
        width: 600px;       
        height: 250px;            
        box-shadow: rgba(0, 0, 0, 0.24) 2px 3px 5px;  
        overflow: hidden;
       


    }

    .presentation__btn{
        position: absolute;
        display: flex;
        align-items: center;
        justify-content: center;
        right: 20%;
        top: calc(50% - 10px);
        background-color: transparent;
        border:0.1px solid gainsboro;
        font-size: var(--text_xxxl);
        cursor: pointer;
        border-radius: 100%;
        height: 30px;
        width: 30px;
        color:rgb(226, 226, 226);
        transition: all var(--time1) ease;
    }

    .presentation--left{
        left: 20%;
    }

    .presentation__btn:hover{
        background-color: rgb(238, 238, 238);
        color: white;
        box-shadow: rgba(0, 0, 0, 0.24) 2px 3px 5px;  
    }
    
    .presentation__img{
        width: 100%;
        object-fit:cover;
        transition: all var(--time1) ease-in-out;      
        cursor: pointer;
        height: 250px;
        
    }

    /** texte d'information sur le developpement */
    .presentation__text-container{
        position: relative;
        width: 100%;
        background-color: white;
        height: 250px;
        transition: all var(--time1) ease;

    }

    .presentation_text-closed{
        position: absolute;
        display: flex;
        align-items: center;
        justify-content: center;
        right: 10px;
        top:10px;
        border:0.5px solid lightgray;
        border-radius: 100%;
        width: 25px;
        height: 25px;
        font-size: var(--text_xl);
        cursor: pointer;
        color: red;
        transition: all var(--time1) ease;
        
    }
    
    .presentation_text-closed:hover{
        box-shadow: rgba(0, 0, 0, 0.24) 2px 3px 5px;
        transform: scale(1.1);
    }

    .presentation__techno-list{      
        display: flex;
        align-items: center;
        justify-content: space-around;
        transition: all var(--time1) ease;
        width: 100%;
        padding: 10px 0px;
        font-weight: 800;
        font-size: var(--text_xs);
        text-transform: uppercase;
    }

    .presentation__techno-item{
        background-color: tomato;
        padding: 5px;
        color: white;
        border-radius: 10px;


    }

    .presentation__comment-list{
        padding:25px ;
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        list-style-type: disc;
        list-style-position: inside;
        line-height: 2;
        font-weight: 700;
        text-transform: uppercase;
        font-size: var(--text_s);

    }
  
    


    
</style>