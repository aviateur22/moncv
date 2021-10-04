<template>
  <div class="container">
      <h2 class="title">mon parcours</h2>
      <!-- reconvertion professionel -->
      <section>          
          <article class="article">
              <!-- conteneur date et echelle -->
              <header>
                  <div class="article__header">
                      <h3 class="article__header-title">
                          <p>aujourd'hui </p>
                          <p>à </p>
                          <p>2021</p>
                      </h3>
                  </div>
              </header>
              <main class="article__content">
                  <h2 class="article__content-title">reconversion professionnelle</h2>
                  <p class="article__content-text">
                    .HTML/CSS/Javascript
                    .React & NodeJS
                    .modélisation et implémentation de base de données
                    .Gestion de projet avec la méthodologie AGILE
                    .Déploiement sur serveur
                    .réalisation complète d’une application WEB 
                  </p>
              </main>
          </article>
      </section>

      <!-- reconvertion professionel -->
      <section>
          <article class="article">
              <!-- conteneur date et echelle -->
              <header>
                  <div class="article__header">
                      <h3 class="article__header-title">
                          <p>2021</p>
                           <p>à</p>
                            <p>2013s</p>
                      </h3>
                  </div>
                  
              </header>
              <main class="article__content">
                    <h2 class="article__content-title">autodidacte</h2>

                    <p class="article__content-text">
                        Pationné par le développement WEB et logiciel:
                        .C#
                        .WPF
                        .JAVASCRIPT
                        .VUEJS
                    </p>
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
    }
    .title{
        text-transform: uppercase;
        font-weight: var(--text-bold);
        font-size: var(--text_xxl);
        color: var(--title_color);
        padding: 25px 0px;
        
    }
    .article{
        padding: 20px 0px;
        display: flex;
        

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
        max-width: 700px;
        padding: 0px 25px;
        background-color: #F6F6F6;
    }

    .article__content-title{
        text-transform: uppercase;
        font-weight: var(--text-bolder);
        padding: 20px 0px;

    }

</style>