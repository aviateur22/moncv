<template>
  <div id="myExperience" class="container">
      <h2 class="title">mon parcours</h2>

       
      <!-- reconvertion professionel -->
      <section class="article__section">  
          <!-- repere temporel -->
          <div class="time-line"></div>        

          <article class="article">
              <!-- conteneur date et echelle -->
              <header class="article__header">
                    <h3 class="article__header-title">
                          <p>aujourd'hui </p>
                          <p>à </p>
                          <p>2021</p>
                    </h3>  

                   

              </header>
              <main class="article__content">
                  <h2 class="article__content-title">reconversion professionnelle</h2>
                  <h2 class="article__content-date mobile"> aujourd'hui à 2021</h2>
                  <h2 class="article__content-date"></h2>
                  <ul class="article__list">
                      <li><p class="article__list-item">HTML/CSS/Javascript</p></li>
                      <li><p class="article__list-item">React & NodeJS</p></li>
                      <li><p class="article__list-item">modélisation et implémentation de base de données</p></li>
                      <li><p class="article__list-item">Gestion de projet avec la méthodologie AGILE</p></li>
                      <li><p class="article__list-item">Déploiement sur serveur</p></li>
                      <li><p class="article__list-item">réalisation complète d’une application WEB </p></li> 
                  </ul>
              </main>
          </article>
      </section>

      <!-- reconvertion professionel -->
      <section class="article__section">
          <article class="article">
              <!-- repere temporel -->
            <div class="time-line"></div>  

              <!-- conteneur date et echelle -->
              <header class="article__header">
                    <h3 class="article__header-title">
                        <p>2021</p>
                        <p>à</p>
                        <p>2013</p>
                    </h3>                  
              </header>
              <main class="article__content">
                    <h2 class="article__content-title">autodidacte</h2>
                    <h2 class="article__content-date mobile"> de 2021 à 2013</h2>
                    <p class="article__content-text"> Pationné par le développement WEB et logiciel: </p>
                    <ul class="article__list">
                        <li><p class="article__list-item">C#</p></li>
                        <li><p class="article__list-item">WPF</p></li>
                        <li><p class="article__list-item">JAVASCRIPT</p></li>
                        <li><p class="article__list-item">VUEJS</p></li>
                        <li><p class="article__list-item">VBA</p></li>
                        <li><p class="article__list-item">VB</p></li>
                        <li><p class="article__list-item">G A S</p></li>
                    </ul>                    
              </main>
          </article>
      </section>
  </div>
</template>

<script>
export default {
    name:'ProfessionnalExperience'

}
</script>

<style scoped>
@media (max-width:768px){
    
    .article__content{    
        margin: 10px 10px !important;
    }

    .article__content-date{
       display: block !important;
    }

    .article__header{
        display: none !important;
    }
    
    .article__content::before{    
        display: none !important;
    }

    .time-line{
        display: none !important;
    }

    .time-line::before{
       display: none !important;
    }
}
    .container{
        max-width: 768px;
        margin: 0px auto;
       
    }

    .title{
        text-transform: uppercase;
        font-weight: var(--text-bold);
        font-size: var(--text_xxl);
        color: var(--title_color);
        padding: 25px 0px;
        text-align: center  ;
        
    }    

    .article__section{
         position: relative;
    }

    .time-line{
        position: absolute;
        width: 5px;
        background-color: #EBEBEB;
        top: 0px;
        bottom: 0px;
        left: 130px;
        box-shadow: rgba(0, 0, 0, 0.24) 1px 2px 1px;
    }

    .time-line::before{
        content: " ";
        position: absolute;
        width: 25px;
        height: 25px;
        left: -10px;
        background-color: #f0f0f0;
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 5px;
        top: calc(50% - 12px);
        border-radius: 50%;
    }

    .article{
        padding: 20px 0px;
        display: flex;        
    }

    .article__header{
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;

    }    
    
    .article__header-title{        
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 0px 20px;
        width: 100px;
        color: var(--date_color);

    }

    .article__content{
        position: relative;
        width: 700px;
        padding: 0px 35px;
        background-color: #F6F6F6;
        line-height: 2;
        padding-bottom: 20px;
        border-radius: 10px;
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
        margin-left: 20px;
    }

    .article__content::before{    
        content: "";
        position: absolute;
        width: 20px;
        height: 20px;
        border-top: 1px solid;
        border-left: 1px solid;
        top: calc(50% - 10px);
        left: -10px;
        background: var(--title_color);
        transform: rotate(45deg);
        z-index: -1;
    }

    .article__content-title{
        text-transform: uppercase;
        font-weight: var(--text-bolder);
        padding: 20px 5px;
        /* display: inline-block; */
    }

    .article__content-date{
        font-weight: var(--text-bolder);
        padding: 20px 0px;
        display: inline-block;
        color: rgb(177, 177, 177);
        font-size: var(--text_l);
        display: none;
    }

    .article__list{
        list-style-type: disc;
        padding-left: 50px;
    }

</style>