<template>
  <article class="project">
       <div ref="projectInner" @click="projectInnerClick" class="project__inner">
            <section class="project__front">     
                <div class="project__container">
                    <img :src="this.getImg(this.project.imgs)" alt="" class="project__img"/>
                    <div ref="projectInfoContainer" class="project__info-container project__container--blur">
                        <div class="project__name">
                            <h2 class="project__name-title"> {{ this.project.name }} </h2>
                        </div>

                        <!-- date de création -->
                        <div class="project__date">
                            <p class="project__date-text">
                                {{ this.project.date }}
                            </p>
                        </div>
                    </div>
                </div>
            </section>
            <section class="project__back">
                <div class="project__presentation-back">
                    <img :src="this.getImg(this.project.imgs,this.imgId2)" alt="" class="project__img-back"/>                    
                    <div class="project__techno-container">
                        <h2 class="project__name">{{ this.project.name }}</h2>
                        <!-- techno utilisé -->
                        <ul class="project__techno-list">
                            <li class="project__techno-item" v-for="techno,id in this.project.technos" :key="id">
                                {{ techno }}
                            </li>
                        </ul>
                    </div>    
                    <div class="project__comment-container">
                        <ul class="project__comment-list">
                            <li class="project__comment-item" v-for="comment,id in this.project.comments" :key="id">
                                <p>{{ comment }}</p>
                            </li>
                        </ul>
                    </div>
                </div>
            </section>              
        </div>
  </article>
</template>

<script>
export default {
    name:'projectDisplay2',
    props:['project'],
    data(){
        return{
            imgId1 : 0,
            imgId2 :1
        }
    },
    methods:{
         /**
         * Renvoie l'url de l'image utilisable par VUEJS
         */
        getImg(imgDataArray,img = this.imgId1){

            try{
                return require('../../assets/images/github/'+ imgDataArray[img].imgName);
            }
            catch(err){
               
                console.log(err)
            }
            
          
        },

        /**
         * Rotation du projet 
         */
        projectInnerClick(){
            const projectInner = this.$refs.projectInner;
            const projectInnerFrontInfoContainer = this.$refs.projectInfoContainer;
            projectInner.classList.toggle('flipped');
            setTimeout(()=>{
                projectInnerFrontInfoContainer.classList.toggle('project__container--blur');
            },300)
            

        }
    }

}
</script>

<style>

.project{    
    perspective: 1000px;  
    padding: 10px;
    min-width: 320px;
    max-width: 320px;
    height: 420px;    
    margin: 10px;
    width: calc(25% - 20px);
    box-sizing: border-box;
}

.project__inner{
    position: relative;
    cursor: pointer;
    transition: transform var(--time3);
    transform-style: preserve-3d;
    width: 100%;
    height: 100%;
}

.project__front , .project__back {
    position: absolute;
    display: flex;    
    flex-direction: column;
    height: 100%;
    width: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
    border-radius: 5px;
   
}

.flipped{
    transform: rotateY(180deg);
}

.project__container{
    position: relative;
    overflow: hidden;
    transform-style: preserve-3d;
    height: 100%;
    border-radius: 5px;
    
}

.project__img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position:left top;
}

.project__info-container{
    position: absolute;
    bottom: 0px;
    left: 0px;
    width: 100%;
    height: 100px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;    
    border-top: 1px solid gray;
}

.project__container--blur{
    backdrop-filter: blur(4px)
}

.project__name{
    margin: 10px;
    align-self: flex-start;
    text-align: center;
    border: 1px solid white;
    background-color: rgba(105, 108, 112, 1);
    color: white;
    font-weight: var(--text-bolder);
    text-transform: uppercase;
    padding: 10px;       
    border-radius: 5px;
    box-shadow: rgba(0, 0, 0, 0.24) 2px 3px 5px;
    text-shadow: 1px 1px 2px black, 0 0 1em rgb(70, 69, 69), 0 0 0.2em rgb(107, 107, 107); 
    z-index: 0;
    
}

.project__date{
    align-self: flex-end;
    margin: 10px;
    border: 1px solid white;
    text-align: center;
    background-color: #444344;  
    color: white;      
    font-weight: var(--text-bolder);
    text-transform: uppercase;
    transform: translateX(0px);
    transition: all var(--time1) ease-in-out;
    padding: 5px 30px;
    opacity: 1;
    border-radius: 5px;
    z-index: 0;    
}

.project__back{
    transform: rotateY(180deg);    
    overflow: hidden;
}

.project__presentation-back{
    position: relative;
    
}

.project__img-back{
    width: 100%;
    height: 200px;
    object-fit: cover;
    object-position: left top;
    border-bottom: 1px solid lightgrey ;
 
}

.project__name-back-title{
    font-size: var(--text_xl);
}

.project__techno-container{
    position: absolute;
    top: 0px;
    right: 0px;
    left: 0px;

}

.project__techno-list{          
    display: flex;
    align-items: center;
    justify-content: space-around;
    flex-wrap: wrap;    
    transition: all var(--time1) ease;
    width: 100%;
    padding: 10px 0px;
    font-weight: 800;
    font-size: var(--text_s);
    text-transform: uppercase;
    
    }

.project__techno-item{
    background-color: tomato;
    padding: 5px;
    color: white;
    border-radius: 10px;
    margin-bottom: 5px;
    
    
}

.project__comment-container{
    overflow-y: auto;
    height: 190px;


}

.project__comment-list{ 
    
    padding:25px ;
    display: inline-flex;
    flex-direction: column;   
    flex-wrap: nowrap;
    list-style-type:disc;
    list-style-position:outside;
    line-height: 2;
    font-weight: 600;
    text-transform: uppercase;
    font-size: var(--text_xs);
    max-width: 100%;
}

.project__comment-item{
    margin: 10px 0px;
}

</style>