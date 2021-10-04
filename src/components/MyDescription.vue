<template>
  <div id="MyDescription" class="description">
      <section class="description__story">
          <h2 class="description__story-title">a propos de moi</h2>
          <p class="description__story-content">
              Lorem ipsum dolor sit amet consectetur, adipisicing elit. Magni voluptates deserunt id nostrum dolore. Totam, atque sapiente quis ratione doloremque est! Libero alias natus nihil!
          </p>
      </section>
      <section class="description__profil">

      </section>
      
  </div>
</template>

<script>
export default {
    name:'MyDescription'
}
</script>

<style scoped>
.description{
    padding: var(--padding_block);
    background-color: #F6F6F6;
    margin-top: 50px;;
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