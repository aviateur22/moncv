<template>
<div class="main-container">
  <div id="MyDescription" class="container">
      <section class="description__story">
          <h2 class="description__story-title">a propos de moi</h2>
          <p class="description__story-content">
              Lorem ipsum dolor sit amet consectetur, adipisicing elit. Magni voluptates deserunt id nostrum dolore. Totam, atque sapiente quis ratione doloremque est! Libero alias natus nihil!
          </p>
      </section>
      <section class="description__profil">

      </section>      
  </div>
</div>
   <!--container pour centrer les élémént -->

</template>

<script>
export default {
    name:'MyDescription'
}
</script>

<style scoped>

.main-container{
    background-color: #F6F6F6;       
    margin-top: 50px;;
}

.container{
    max-width: 768px;
    margin: 0px auto; 
}

.description__story{
    max-width: 70%;
}

.description__story-title{
    text-transform: uppercase;
    font-weight: var(--text-bold);
    font-size: var(--text_xxl);
    color: var(--title_color);
    padding: 25px 0px;
}

</style>