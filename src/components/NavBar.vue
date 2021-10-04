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
                    <h2><a class="header__navlink" href="#MyDescription">mon parcours</a></h2>
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
        padding: var(--padding_navbar);
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
        font-weight: var(--text-bolder);
        font-size: var(--text_xxxl);        
        padding: 15px 0px;
        text-shadow: 1px 1px 2px black, 0 0 1em black, 0 0 0.2em black;
        color: white;

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
        font-weight: bold;
        color: var(--menu_color);
        font-size: var(--text_xl);
        cursor: pointer;
        transition: all var(--time1) ease-in-out;
    }

    .header__navlink:hover{
          font-size: var(--text_xs);

    }

    

</style>