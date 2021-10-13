<template>
<div class="main-container">
     <h2 class="description__story-title">a propos de moi</h2>
  <div id="MyDescription" class="container">
      <section class="description__story">
         
            <p class="description__story-content">
              Je suis autodidacte et pationné en développement Web et logiciel depuis quelques années. Aujourd'hui, je franchis le pas, je commence une reconversion professionnelle pour devenir développeur Web.  
            </p>
            <p class="description__story-content">
              Mon travail actuel m'a permis d'acquérir autonomie et le goût d'être en équipe. 
              Mes rèsponsables mon fait confiance et j'ai ainsi eu l'occasion de proposer, développer et de mettre en place certains logiciels.
            </p>
            <p class="description__story-content">
              Je suis de nature curieux et j'aime apprendre. Mon défis actuel est l'apprentissage de VUEJS.         
            </p>


         
      </section>
      <section class="description__profil">
          <div class="profil__container">
              <div class="profil__bubble">
                  <Bubble :data="bubbleInformation"/>
              </div>
              
              <img src='../assets/images/github/avatar.png' alt="my beautiful picture" class="profil__img">              
              <div class="description__detail-container">
                  <h2 class="description__name"> <span class="description__name-category"> nom:  </span> Cyrille Cadé</h2>
                  <h2 class="description__name"> <span class="description__name-category">age:</span> 37 ans</h2>
                  <h2 class="description__name"> <span class="description__name-category" >ville:</span> Auterive 31190</h2>                  
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
    data(){
        return{
            bubbleInformation:{
                title:"Ma situation personnelle",
                text:"je suis en couple, avec 2 enfants"
            }
        }
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