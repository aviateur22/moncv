<template>
  <div id="myExperience" class="container">
      <h2 class="title">mon parcours</h2>

       <div class="time-line"></div>
      <!-- reconvertion professionel -->
      <section>          
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
      <section>
          <article class="article">
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
                    <p class="article__content-text"> Pationné par le développement WEB et logiciel: </p>
                    <ul class="article__list">
                        <li><p class="article__list-item">C#</p></li>
                        <li><p class="article__list-item">WPF</p></li>
                        <li><p class="article__list-item">JAVASCRIPT</p></li>
                        <li><p class="article__list-item">VUEJS</p></li>
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
    .container{
        padding: var(--padding_block);
        position: relative;
    }
    .title{
        text-transform: uppercase;
        font-weight: var(--text-bold);
        font-size: var(--text_xxl);
        color: var(--title_color);
        padding: 25px 0px;
        
    }
    .time-line{
        position: absolute;
        width: 5px;
        background-color: #EBEBEB;
        top: 150px;
        height: 680px;
        left: 155px;
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
        background: #6666b3;
        transform: rotate(45deg);
        z-index: -1;
    }

    .article__content-title{
        text-transform: uppercase;
        font-weight: var(--text-bolder);
        padding: 20px 0px;
    }

    .article__list{
        list-style-type: disc;
        padding-left: 50px;
    }

</style>