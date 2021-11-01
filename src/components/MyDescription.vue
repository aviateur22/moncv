<template>
<div class="main-container">
     <h2 class="description__story-title">a propos de moi</h2>
  <div id="MyDescription" class="container">
      <section class="description__story">
         
            <p class="description__story-content">
                {{ this.myDescription.presentationItem1 }}
            </p>
            <p class="description__story-content">
                {{ this.myDescription.presentationItem2 }}
            </p>
            <p class="description__story-content">
                {{ this.myDescription.presentationItem3 }}
            </p>


         
      </section>
      <section class="description__profil">
          <div class="profil__container">
              <div class="profil__bubble">
                  <Bubble :data="bubbleInformation"/>
              </div>
              
              <img src='../assets/images/github/mypicture.png' alt="my beautiful picture" class="profil__img">              
              <div class="description__detail-container">
                  <h2 class="description__name"> <span class="description__name-category"> nom:  </span> {{ this.myDescription.name }} {{ this.myDescription.lastName }} </h2>
                  <h2 class="description__name"> <span class="description__name-category">age:</span> {{ this.myCalculatedAge }} ans</h2>
                  <h2 class="description__name"> <span class="description__name-category" >ville:</span>  {{ this.myDescription.city }}  {{ this.myDescription.zipCode }} </h2>                  
              </div>

          </div>
      </section>      
  </div>
</div>
   <!--container pour centrer les élémént -->

</template>

<script>
import Bubble from './bubble/InformationBubble.vue'
export default {
    name:'MyDescription',
    components:{
        Bubble
    },
    props:['myDescription'],
    data(){
        return{
            myCalculatedAge: -1,
            bubbleInformation:{
                title:"Ma situation personnelle",
                text:"je suis en couple, avec 2 enfants"
            }
        }
    },
    methods:{
        /**
         * Renvoie l'url de l'image utilisable par VUEJS
         */
        getImg(imgDataArray,img = this.imgId1){

            try{
                return require('../assets/images/github/'+ imgDataArray[img].imgName);
            }
            catch(err){
               
                console.log(err)
            }
        },        

        /**
         * Calcul de l'age a partir de la date de naissance
         */
        getAge(){

           /* Element de naissance */ 
           const year =  this.myDescription.birthday.year;
           const month = this.myDescription.birthday.month;
           const day = this.myDescription.birthday.day;

            //Convertion en date
           const birthday = new Date(year,month,day);

           //Calcul de l'age
           this.myCalculatedAge = this.calculate_age(birthday);           

        },

        /**
         * 
         */
        calculate_age(birthday) { 
            var diff = Date.now() - birthday.getTime();
            var age_dt = new Date(diff);        
            return Math.abs(age_dt.getUTCFullYear() - 1970);
        }
    },
    mounted(){
        this.getAge();
    }
}
</script>

<style scoped>

@media(max-width: 768px){
    .main-container{
        margin: 0px 5px;
    }
    .container{
        flex-direction: column !important;
        align-items: center;
    }

    .description__story{      
        max-width:  100% !important;     
    }

    .description__profil{
        margin-top: 20px !important;
        min-width: 100% !important
    }

    .profil__container{
        flex-direction: column !important;
    }

    .profil__img{
        margin-bottom: 20px;
    }


}

.main-container{
    background-color: #F6F6F6;       
    margin-top: 5px;;
}

.container{
    max-width: 900px;
    margin: 0px auto; 
    display: flex;
    align-items: center;
}

.description__story{
    max-width:  50%;
    padding-left: 10px;
    padding-right: 45px;
}

.description__story-title{
    text-align: center;
    text-transform: uppercase;
    font-weight: var(--text-bold);
    font-size: var(--text_xxl);
    color: var(--title_color);
    padding: 25px 0px;
}

.description__story-content{
    line-height: 1.5;
    text-align:justify;
    word-break:keep-all;
    padding-bottom: 25px;
   
}

/* PROFIL  */
    .description__profil{
        flex-grow:3;
        padding-bottom: 20px;
        width: 50%;
    }

    .profil__container{
        position: relative;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        
    }

    .profil__bubble{
        position:absolute;
        top: calc(0%);
        right:calc(0%);
    }

    .profil__img{
        width: 150px;
        height: 150px;
        border: 3px solid gainsboro;
        border-radius: 100%;
        object-fit: cover;
        
    }
    .description__detail-container{        
        padding: 0px 20px;
    }

    .description__name-category{
        text-transform: uppercase;
        font-weight: normal;
        font-size: var(--text_s);
        margin-right: 5px;        
    }
    .description__name{
        text-transform: uppercase;
        font-weight: var(--text-bold);
        font-size: var(--text_l);
        line-height: 2;
        color: var(--menu_color);

    }

</style>