<template>
<div class="container">
    <header class="header">      
        <nav class="header__navbar">
            <!-- zone de titre -->
            <section class="header__title-container">
                <!-- titre -->
                <h1 class="header__title">DEVELOPPEUR WEB FULLSTACK JAVASCRIPT</h1>
            </section>

            <!-- zone de navigation -->
            <section class="header__navigation-container">
                <div class="header__profile-picture">
                    <img src="../assets/images/profile.jpg" alt="ma photo">
                </div>

                <!-- liens de navigation  -->
                 <div class="header_navlink-container">
                    <img class="header_navlink-picture" src="../assets/images/logo.png" alt="ma photo">
                    
                </div>

                <div class="header_navlink-container">
                    <img class="header_navlink-picture" src="../assets/images/html.png" alt="ma photo">
                    <h2><a class="header__navlink" href="#me">mon parcours</a></h2>
                </div>
                
                <div class="header_navlink-container">
                    <img class="header_navlink-picture" src="../assets/images/javascript.png" alt="ma photo">
                    <h2><a class="header__navlink" href="#me">mes technos</a></h2>
                </div>

                <div class="header_navlink-container">
                    <img class="header_navlink-picture" src="../assets/images/css.png" alt="ma photo">
                    <h2><a class="header__navlink" href="#me">mes projets</a></h2>
                </div>                
            </section>  
            <!-- image -->
            

        </nav>
  </header>
</div>
  
</template>

<script>
export default {

    name:'Navigation'

}
</script>

<style scoped>

    .container{
        max-width: 880px;
        margin: 0px auto;
    }

    .header__navbar{
        display: flex;
        flex-direction: column;
    }

    .header__title-container{
        display: flex;
        justify-content: flex-start;

    }

    .header__title{
        font-weight: 800;
        font-size: var(--text_xxxl);
        padding: 15px 0px;

    }

    .header__navigation-container{      
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .header_navlink-container{
          position: relative;
          display: flex;
          justify-content: center;
          align-items: center;
          height: 155px;
          width: 155px;
          
    }

    .header_navlink-picture{
        position: absolute;
        max-width: 100%;
        left: 0px;
        top: 0px;
        opacity: 0.1;
        z-index: -1;

    }

    .header__navlink{
        text-transform: uppercase;
        text-decoration: none;
        font-weight: 600;
        color: black;
        font-size: var(--text_xl);
        cursor: pointer;
        transition: all var(--time1) ease-in-out;
    }

    .header__navlink:hover{
          font-size: var(--text_xs);

    }

    

</style>