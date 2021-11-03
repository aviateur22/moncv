<template>
   <article class="article">
        <header class="article__title">
                <h2 class="article__title-content">{{ techno.title }}</h2>
        </header>
        <main class="article__content">
            <ul class="article__list">
                <li v-for="(item,id) in techno.items" :key="id" ><p class="article__list-item"> {{ item }}</p></li>
            </ul>    
            <img :src="this.getImg(this.techno.image)" alt="" class="article__img">
        </main>        
    </article>
</template>

<script>
export default {
    name:'techno',
    props:['techno'],
    mounted(){
         console.log(this.techno)
    },
    methods:{
        /**
         * Renvoie l'url de l'image utilisable par VUEJS
         */
        getImg(img){

            try{
                return require('../../assets/images/github/'+ img);
            }
            catch(err){               
                console.log(err)
            }
        },
    }

}
</script>

<style scoped>

@media(max-width:768px) { 
    .article{
        margin: 10px 0px !important;
    }    
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