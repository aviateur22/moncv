<template>
<div class="main-container">
     <h2 class="description__story-title">a propos de moi</h2>
  <div id="MyDescription" class="container">
      <section class="description__story">
         
          <p class="description__story-content">
              Lorem ipsum dolor sit amet consectetur, adipisicing elit. Magni voluptates deserunt id nostrum dolore. Totam, atque sapiente quis ratione doloremque est! Libero alias natus nihil!
          </p>
      </section>
      <section class="description__profil">
          <div class="profil__container">
              <img src='../assets/images/profile.png' alt="ma photo de profil" class="profil__img">
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
export default {
    name:'MyDescription'
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

    .description__profil{
        margin-top: 20px !important;
        min-width: none !important
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
    margin-top: 50px;;
}

.container{
    max-width: 900px;
    margin: 0px auto; 
    display: flex;
    align-items: center;
}

.description__story{
    flex-grow: 0;
    max-width: 500px;
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
   
}

/* PROFIL  */
    .description__profil{
        flex-grow:3;
        padding-bottom: 20px;
        min-width: 320px
    }

    .profil__container{
        display: flex;
        justify-content: flex-start;
        align-items: center;
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
        font-size: var(--text_xl);
        line-height: 2;
        color: var(--menu_color);

    }

</style>