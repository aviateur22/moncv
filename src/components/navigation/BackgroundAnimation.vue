<template>
  <div class="animation-container">
       <span ref="darkWord" :data-color-word="this.WordArrayActif" class="dark__word">{{ this.copyDarkWord }}</span>

       <span ref="colorWord" class="color__word">{{ this.copyColorWord}}</span>
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
                    "colorWord" :"développeur",
                    "array":["web","fullstack","javascript"]
                },
                {
                    "darkWord":"j'aime",
                    "colorWord" :"travailler avec",
                    "array":["vuejs","nodejs","react",'html','css',"mongodb","sqlite"]
                }
            ],
            darkWord:undefined,  
            copyDarkWord:undefined,          
            colorWord:undefined,
            copyColorWord:undefined,
            WordArrayActif:undefined,
            main_index:0,
            secondary_index:0,
            timeAnimation:5000,
        }    
    },
    methods:{

        init(){
                this.darkWord = this.data[this.main_index].darkWord;
                this.copyDarkWord = this.darkWord;                
                this.colorWord = this.data[this.main_index].colorWord
                this.copyColorWord =this.colorWord;
                this.updateWordArray();               
        },

        updateWordArray(){
            const action = setInterval(()=>{    
                
                this.WordArrayActif=this.data[this.main_index].array[this.secondary_index]     ;
                this.secondary_index++;           
                this.secondary_index = this.secondary_index < this.data[this.main_index].array.length ?  this.secondary_index++ : 0 ;
                if(this.secondary_index===0){                  
                    
                    setTimeout(()=>{      
                        this.$refs.darkWord.style.opacity =0;
                        this.$refs.colorWord.style.opacity =0;                
                        this.main_index++;
                        this.main_index = this.main_index < this.data.length ?  this.main_index++ : 0  ;            
                        this.darkWord = this.data[this.main_index].darkWord;
                        this.colorWord = this.data[this.main_index].colorWord;
                    },this.timeAnimation-500)
                }
            }, this.timeAnimation)
        }
    },
    created(){
        this.init()
    },
    watch:{
        /**Gestion de l'affichage d'un projet à l'autre */
        darkWord: function (){
            
            if(this.$refs.darkWord){
                
                

                setTimeout(()=>{
                    this.copyDarkWord=this.darkWord;
                    this.copyColorWord = this.colorWord;                    
                    this.$refs.darkWord.style.opacity =1;
                    this.$refs.colorWord.style.opacity =1;
                },300)
            }
            
          
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
        top: 50px;        
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