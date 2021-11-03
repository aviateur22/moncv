<template>
  <div :class="{'show':this.show}" id="techno" class="container">
      <h2 class="title">techno</h2>
        <div class="container-article">
            <section v-for="( techno, id ) in technos" :key="id">
                <TechnoDisplay :techno="techno"/>
            </section>
            <!-- <section>
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
            </section> -->
        </div>      
  </div>
</template>

<script>
import TechnoDisplay from './techno/TechnoDisplay.vue';
export default {
    name:'Techno',
    components:{
        TechnoDisplay
    },
     mounted(){
        window.addEventListener('scroll', this.onScroll)       
    },
    data(){
        return{
            show:false
        }
    },
    props:['technos'],
    methods:{

    /**Gestion du défilement de la souris */
    onScroll(){
            // Position du scroll
        const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop

        // Affichage élémént = 600px
        if (currentScrollPosition > 700) {
            this.show = true;            
        }
        this.lastScrollPosition = currentScrollPosition;        

    },
        
    },

}
</script>

<style scoped>
@media(max-width:768px) {

    .container-article{
        flex-direction: column !important;
        align-items: center !important;
        margin:5px !important
        
    }

 
}

.container{
    background-color: #F6F6F6;   
    margin-top: 40px;
    padding-bottom: 40px;
    transition: all var(--time2) cubic-bezier(0.39, 0.575, 0.565, 1);
    opacity: 0;
}

.container-article{
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    max-width: 1200px;
    margin:0px auto;
}

.title{
    text-transform: uppercase;
    font-weight: var(--text-bold);
    font-size: var(--text_xxl);
    color: var(--title_color);
    padding: 25px 0px;
    text-align: center;
}



.show{
    opacity: 1 !important; 
    transform: translate3d(0, -10px, 0) !important;    
}    
</style>
