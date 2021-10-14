<template>
  <div :class="{'show' : this.show}" id="contact" class="container">
      <h2 class="title">contact</h2>

      <p class="text"><span class="strong">Vous souhaitez me rencontrer</span>, je suis disponible sur Auterive et ses alentous</p>
      <p class="text space">A bientôt </p>
      <div class="contact-container">
          <section class="contact">
                <h4><a href="tel:0623274101" class="contact__content">06 23 27 41 01</a></h4>
          <h5></h5>
      </section>
      <section class="contact contact--mail">            
            <h4><a href="mailto:aviateur22@hotmail.fr" class="contact__content contact__content--mail">aviateur22@hotmail.fr</a></h4>
      </section>
      </div>      
  </div>
</template>

<script>
export default {
    name:'Contact',
    mounted(){
        window.addEventListener('scroll', this.onScroll)
    },
    data(){
        return{
            show:false
        }
    },
    methods:{

        /**Gestion du défilement de la souris */
        onScroll(){
             // Position du scroll
            const currentScrollPosition = window.pageYOffset || document.documentElement.scrollTop

            // Affichage composant = 50px
            if (currentScrollPosition > 1600) {
                this.show = true;
            
            }
            this.lastScrollPosition = currentScrollPosition;      

        }
    }
}
</script>

<style scoped>
@media(max-width: 768px){
    .contact-container{
        flex-direction: column !important;
        align-items: center;
        justify-content: center;
    }

    .contact{
        margin: 15px 0px !important;
    }

    .contact__content{
        font-size: var(--text_l) !important;
       
    }


}
    .container{
        margin-bottom: 40px;
        transition: all var(--time2) cubic-bezier(0.39, 0.575, 0.565, 1);
        opacity: 0;
    }

    .show{
      opacity: 1 !important; 
      transform: translate3d(0, -10px, 0) !important;
    }

    .title{
        text-transform: uppercase;
        font-weight: var(--text-bold);
        font-size: var(--text_xxl);
        color: var(--title_color);
        padding: 25px 0px;
        text-align: center  ;
    }

    .text{
        text-align: center;
    }

    .strong{
        font-weight: 800;
    }

    .space{
        margin: 50px 0px;
    }

    .contact-container{
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .contact{
        background-image: url('../assets/images/github/phone.svg');
        background-repeat: no-repeat;
        background-size: 25%;
        background-position: 50%;
        background-color: rgba(140, 255, 148,0.9);
        border-radius: 10px;
        width: 300px;
        padding: 20px 0px;
        margin: 0px 10px;
        box-shadow: rgba(0, 0, 0, 0.20) 0px 3px 5px;
        transition: all var(--time1) ease-out;
    }

    .contact:hover{
        box-shadow: rgba(0, 0, 0, 0.80) 0px 3px 5px;
    }
    .contact__category{
        text-transform: uppercase;
        font-weight: var(--text-bolder);
        padding: 20px 5px;
    }

    .contact--mail{
        background-image: url('../assets/images/github/mail.svg');
        background-color: rgba(158, 242, 255,0.8);
        text-shadow: 1px 1px 2px black;
    }

    .contact__content{
        display: block;
        text-align: center;
        font-size: var(--text_xxl);
        font-weight: var(--text-bolder);
        padding: 20px 5px;
        text-decoration: none;
        color: green;
        text-shadow: 1px 1px 2px black;
    }

    .contact__content--mail{
        color: #4f75ff;
    }
</style>