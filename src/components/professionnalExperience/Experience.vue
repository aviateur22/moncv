<template>
  <div class="article__section">  
          <!-- repere temporel -->
          <div class="time-line"></div>        

          <article class="article">
              <!-- conteneur date et echelle -->
              <header class="article__header">
                    <h3 class="article__header-title"> {{ experience.date }}</h3>                     
              </header>
              <main class="article__content">
                  <h2 class="article__content-title"> {{ experience.title }} </h2>
                  <h4 class="article__content-subTitle"> {{ experience.subTitle}} </h4>
                  <h2 class="article__content-date mobile"> {{ experience.date }}</h2>
                  <h2 class="article__content-date">{{ experience.subTitle }}</h2>                  
                  <ul v-for="(item,id) in experience.items" :key="id" class="article__list">
                      <li><p class="article__list-item">{{ item }} </p></li>
                  </ul>
              </main>
          </article>
      </div>
</template>

<script>
export default {
    name:'Experience',
    props:[
        'experience'
    ]

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

    .article__section{
         position: relative;
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

    .article__content-subTitle{
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