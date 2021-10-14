<template>
  <div class="animation-container">
       <span ref="darkWord" :data-color-word="this.WordArrayActif" class="dark__word"></span>

       <!-- <span ref="colorWord" class="color__word"></span> -->
  </div>
</template>

<script>
export default {
    name:'Animation',
    data(){
        return{
            data:[
                {
                    "darkWord":"je suis",
                    "colorWord" :"futur développeur",
                    "array":["web","fullstack","javascript"]
                },
                {
                    "darkWord":"j'aime",
                    "colorWord" :"travailler avec",
                    "array":["vuejs","nodejs","react",'html','css',"mongodb","sqlite"]
                }
            ],
            darkWord:null,              
            colorWord:undefined,            
            WordArrayActif:undefined,
            main_index:0,
            secondary_index:0,
            timeAnimation:5000,
        }    
    },
    methods:{

        init(){
                /**Affichage du titre principal  */
                this.colorWord = this.data[this.main_index].colorWord;
                this.darkWord = this.data[this.main_index].darkWord;     

                /** Initialise le défilement  des mots autour*/
                this.WordArrayActif=this.data[this.main_index].array[this.secondary_index];
                this.secondary_index++;            

                /**Commence de defilement des mots */
                this.updateWordArray();               

                /**Initialisation du titre*/
                this.updateTitle();
        },

        updateWordArray(){
            const action = setInterval(()=>{    
                
                this.WordArrayActif=this.data[this.main_index].array[this.secondary_index];
                this.secondary_index++;           
                this.secondary_index = this.secondary_index < this.data[this.main_index].array.length ?  this.secondary_index++ : 0 ;
                if(this.secondary_index===0){                  
                    
                    setTimeout(()=>{      
                        
                        this.main_index++;
                        this.main_index = this.main_index < this.data.length ?  this.main_index++ : 0; 
                        this.colorWord = this.data[this.main_index].colorWord;           
                        this.darkWord = this.data[this.main_index].darkWord;
                        
                    },this.timeAnimation-500)
                }
                
            }, this.timeAnimation)
        },

        /**Emit sur la parent pour Changer le titre principale */
        updateTitle(){            
            let titleData={
                darkTitle : this.darkWord,
                colorTitle : this.colorWord
            }
            
            this.$emit('updateTitle',titleData)
        }
    },
    created(){
        this.init()
    },
    watch:{
        /**update du titre dans le parent */
        darkWord: function (){
            this.updateTitle();
        }
    }


}
</script>

<style scoped>
@media screen and (max-width:768px) {

    .dark__word{
        font-size: var(--text_xl) !important;           
    }

    .color__word{     
        font-size: var(--text_xl) !important
    }

     .dark__word::after{  
        font-size: var(--text_xl) !important
     
    }
    
}
.animation-container{    
    display: flex;
    justify-content: center;
    padding: 15px;    
    height: 150px;
    position: relative;
    overflow: hidden;
    

}
    .dark__word{
        color: rgb(160, 160, 160);
        font-size: var(--text_xxxxl);
        font-weight: 900;
        text-transform: uppercase;       
        margin-right: 10px;
        transition: all var(--time1) ease-in;
    }

    .color__word{
        color:var(--title_color);
        font-weight: 800;
        text-transform: uppercase;
        font-size: var(--text_xxxxl);
        transition: all var(--time1) ease-in;

    }

    .dark__word::after{
        text-align: center;     
        text-transform: uppercase;
        position: absolute;
        top: 80px;        
        left:50%;
        transform: translateX(-50%); 
        font-size: 2.0em;
        letter-spacing: 0.5em;
        content: attr(data-color-word);
        text-shadow: 1px 1px 10px black, 0 0 1em rgb(189, 189, 189), 0 0 0.2em rgb(168, 168, 168);
        color: white; 
        z-index: -1;
        animation: animLetterSpacing 5s infinite ease-in-out;
    }

    @keyframes animLetterSpacing {
        0% {
            
            letter-spacing: 2.5em;
            opacity: 0;
        }
        
        40% {
                opacity: 1;
            letter-spacing: 0.5em;
        }
        
        70% {
                letter-spacing: 0.75em;
                opacity: 1;
        }
        
        100% {
            letter-spacing: 2.5em;
            opacity: 0;
        }
    }

</style>