<template>
<hr>
    <h2 class="presentation__title">{{ this.project.name }} </h2>
                    
    <section class="presentation__img-container">  
        <!-- Image de présentation du projet -->
        <img @click="displayInformation" ref="image" class="presentation__img" :src="this.getImg(this.project.imgs)" :alt="this.project.imgs[this.imgId].alt"> 

        <!-- button de défilement des image-->
        <button class="presentation__btn presentation--left" @click="previousImg(this.project.imgs,this.imgId)">&lt;</button>
        <button class="presentation__btn" @click="nextImg(this.project.imgs,this.imgId)">&gt;</button>

        <!-- conteneur d'information sur le developpement -->
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
    <hr class="hr-translate">
</template>

<script>
export default {
    name :'ProjectDisplay',
    data(){
        return{
            imgId:0,
        }
    },
    props:[
        'project'
    ],
    methods:{
         /**
         * Affichage des information de déveloopement au dessus de l'image
         */
        displayInformation(){
            this.$refs.information.style.transform = "translateY(-253px)"
        },

        /**
        *   mesque les informations de déveloopement
        **/

        closedPresentation(){
            this.$refs.information.style.transform = "translateY(0px)"
        },

        /**
         * Renvoie l'url de l'image utilisable par VUEJS
         */
        getImg(imgDataArray){

            try{
                return require('../../assets/images/github/'+ imgDataArray[this.imgId].imgName);
            }
            catch(err){
               
                console.log(err)
            }
            
          
        },

        /**
         * Passe à l'image suivante
         */
        async nextImg(imgDataArray){
            this.rightAnimationEffect();
            setTimeout(() => {     

            this.imgId = this.imgId < imgDataArray.length ? this.imgId++ : 0;            

            this.resetAnimation();

           }, 500);
        },

        /**
         * Passe a l'image précedente
         */
        async previousImg(imgDataArray){

            this.leftAnimationEffect();

            setTimeout(() => {  

                this.imgId = this.imgId > 0 ? this.imgId-- : imgDataArray.length-1; 

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
     
        .presentation__img-container{
            max-width: 320px !important;
        }

         .presentation__btn{
            top: calc(90% - 25px) !important;
        }
    }

    @media(max-width: 1440px){
     
        .presentation__btn{           
            right: 5% !important;            
        }

        .presentation--left{
            left: 5% !important;
        }
    }

    hr { 
        display: block;
        width: 90%;
        box-shadow: rgba(131, 131, 131, 0.5) 2px 1px 5px;  ;
        margin-top: 15px;
    }

    .hr-translate{
        margin-top: 70px;
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
        right: 25%;
        top: calc(50% - 10px);
        background-color: transparent;
        border:0.1px solid gainsboro;
        font-size: var(--text_xxxl);
        cursor: pointer;
        border-radius: 100%;
        height: 30px;
        width: 30px;
        color:rgb(161, 161, 161);
        transition: all var(--time1) ease;
    }

    .presentation--left{
        left: 25%;
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