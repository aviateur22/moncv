<template>
  <div id="techno" class="container">
      <h2 class="title">techno</h2>
        <div class="container-article">
            <section>
                <article class="article">
                    <header class="article__title">
                            <h2 class="article__title-content">back-end</h2>
                    </header>
                    <main class="article__content">
                        <ul class="article__list">
                            <li><p class="article__list-item">C#</p></li>
                            <li><p class="article__list-item">nodejs</p></li>
                            <li><p class="article__list-item">api rest</p></li>
                        </ul>    
                        <img src="../assets/images/github/database.png" alt="" class="article__img">
                    </main>
                    
                </article>
            </section>
            <section>
                <article class="article">
                    <header class="article__title">
                        <h2 class="article__title-content">front-end</h2>
                    </header>
                    <main class="article__content">
                        <ul class="article__list">
                            <li><p class="article__list-item">javascript</p></li>
                            <li><p class="article__list-item">vuejs</p></li>
                            <li><p class="article__list-item">bootstrap</p></li>
                            <li><p class="article__list-item">css</p></li>
                            <li><p class="article__list-item">html</p></li>

                        </ul>  
                        <img src="../assets/images/github/computer.png" alt="" class="article__img">
                    </main>
                    
                </article>
            </section>
            <section>
                <article class="article">
                    <header class="article__title">
                        <h2 class="article__title-content">autres</h2>
                    </header>
                    <main class="article__content">
                        <ul class="article__list">
                            <li><p class="article__list-item">VB</p></li>
                            <li><p class="article__list-item">VBA</p></li>
                            <li><p class="article__list-item">g.a.s</p></li>

                        </ul>  
                        <img src="../assets/images/github/other.png" alt="" class="article__img">
                    </main>
                    
                </article>
            </section>
        </div>      
  </div>
</template>

<script>
export default {
    name:'Techno'

}
</script>

<style scoped>
@media(max-width:768px) {

    .container-article{
        flex-direction: column !important;
        align-items: center !important;
        margin:5px !important
        
    }

    .article{
       margin: 10px 0px !important;
    }
}

    .container{
        background-color: #F6F6F6;   
        margin-top: 40px;
        padding-bottom: 40px;
    }

    .title{
        text-transform: uppercase;
        font-weight: var(--text-bold);
        font-size: var(--text_xxl);
        color: var(--title_color);
        padding: 25px 0px;
        text-align: center;
    }

    .container-article{
        display: flex;
        align-items: flex-start;
        justify-content: space-between;
        max-width: 1200px;
        margin:0px auto;
    }

    .article{
        display: flex;
        flex-direction: column;
        width: 210px;
        border-radius: 10px;
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
        padding: 0px 20px;
        height: 220px;
        background-color: #ffffff;

    }

    .article__title{
        text-transform: uppercase;
        font-weight: var(--text-bolder);
        padding: 20px 5px;

    }

    .article__content{
        display: flex;
        align-items: flex-start;
        justify-content: space-between;

    }

    .article__img{
        order: 1;
        max-width: 30px;
    }

    
    .article__list{
        order: 2;
        padding-left: 20px;
        list-style: disc;
        list-style-position: inside;
        width: 100%;
       
    }

    .article__list-item{
        font-size: var(--text_l);
        text-transform: uppercase;
        line-height: 2;
        display: inline-block;
    }

</style>
