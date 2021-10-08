<template>
  <div class="container">
      <footer class="footer">
          <a href="https://www.linkedin.com/in/cyrille-cade-b58323206/" target="_blank" class="footer__link"> In </a>
      </footer>
    </div>
</template>

<script>
export default {
    name:'FooterLinkedin'

}
</script>

<style scoped>

.container{
    height: 65px;
    background-color: rgb(58, 58, 58);
    display: flex;
    justify-content: center;
    align-items: center;
}
.footer__link{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 30px;
    height: 30px;
    font-weight: 800;
    color: white;
    background-color:#0A66C2;
    border: 2px solid white;
    border-radius: 100%;
    text-decoration: none;
    font-size: var(--text-s);
    transition: all var(--time1) ease;
}

.footer__link:hover{
    transform: scale(1.2);
}

</style>