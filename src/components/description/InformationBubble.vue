<template>
  <div class="container">
      <div class="bubble__outer">
          <div class="bubble__inner">
              <span class="bubble__icone">
                  i
              </span>
            <h2 class="bubble__title">
                {{ data.title }}
            </h2>
            <p class="bubble__text">
                {{ data.text }}
            </p>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name:'Bubble',
    props:[
        'data'
    ]


}
</script>

<style scoped>
.bubble__outer{
    background-color:transparent;   

}

.bubble__inner{
    position: relative;
    padding: 25px 35px;
    clip-path :circle(6% at 94% 18%);
    background-color: transparent;
    cursor: pointer;
    transition: all var(--time1) ease-in-out;
    border-radius: 10px;
}

.bubble__inner:hover .bubble__icone{
    color: var(--title_color);
    border:2px solid var(--title_color);
    
}

.bubble__inner:hover{
    clip-path :circle(150% at 94% 18%);
    background-color: var(--title_color);
}

.bubble__icone{
    display: flex;
    text-align: center;
    justify-content: center;
    position: absolute;
    top:5px;
    right: 5px;
    color: white;
    border:2px solid rgb(199, 199, 199);
    border-radius: 100%;
    width:20px;
    height: 20px;
    background-color: var(--title_color);
    font-size: var(--text_xl);
    font-weight: 500;
    transition: all var(--time1) ease-in-out;

}

.bubble__title{    
    font-size: var(--text_xl);
    font-weight: 700;
    padding-bottom: 15px;
    color:white;
}

.bubble__text{
    font-size: var(--text_s);
    font-weight: 500;
    color: white;

}

</style>