<template>
   <!-- overlay de décoration -->
   <div ref="project" class="project" @click="showPresentation">
       <div class="project__overlay">project{{ project.id +1}}</div>    

        <!-- Nom du projet  -->
        <div class="project__title-border">
            <h2 class="project__title">                    
                <span class="project__title-regular">projet:</span> {{ project.name}}
            </h2>
        </div>
        
        <!-- date de création -->
        <p class="project__date">
            <span class="project__title-regular"> début: </span>  {{ project.date }}
        </p>
   </div>  
    
</template>

<script>
export default {
    name:'ProjectButton',
    data(){
        return{
            previousElement:null,
        }
    },
    props:[
        'project'
    ],
    methods:{

        showPresentation(){                   
            this.$refs.project.style.backgroundColor = '#8c8c8c'
            //affichage du projet en détail
            this.$emit('display-project' , this.project)

            //reset du bouton cliqué précedemment
            this.$emit('reset-color',this.$refs.project)
        }
    },

}
</script>

<style scoped>
 .project{
        margin: 15px 5px;
        position: relative;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width:280px;
        cursor: pointer;
        padding: 25px;
        overflow: hidden;
        box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 5px;
        border-radius: 10px;
        transition: all var(--time1) ease-in;
    }

    .project__overlay{
        display: flex;
        position: absolute;
        top: 0px;
        bottom: 0px;
        left: 0px;
        right: 0px;        
        background-color: rgba(99, 98, 98, 0.4);
        transition: all var(--time1) ease-in;
        color: white;
        text-transform: uppercase;
        align-items: center;
        justify-content: center;
        
    }

    .project__title{
        border: 1px solid white;
        background-color: rgba(105, 108, 112, 0.6);
        color: white;
        font-weight: var(--text-bolder);
        text-transform: uppercase;
        transform: translateX(-500px);
        transition: all var(--time1) ease-in;
        padding: 5px 30px;       
        border-radius: 5px;
        box-shadow: rgba(0, 0, 0, 0.24) 2px 3px 5px;
        text-shadow: 1px 1px 2px black, 0 0 1em rgb(70, 69, 69), 0 0 0.2em rgb(107, 107, 107);
    }

    .project__date{
         border: 1px solid white;
        background-color: #444344;  
        color: white;      
        font-weight: var(--text-bolder);
        text-transform: uppercase;
        transform: translateX(+500px);
        transition: all var(--time1) ease-in-out;
        padding: 5px 30px;
        opacity: 0;

    }
    .project:hover .project__title{
        transform: translateX(0px);
         opacity: 1;
    }

    .project:hover .project__title-border{
        transform: translateX(0px);
         opacity: 1;
    }

    .project:hover .project__date{
        transform: translateX(0px);
        transform: translatey(-5px);
        opacity: 1;
    }

    .project:hover .project__overlay{
        opacity: 0;
    }   

    .project__title-regular{    
        font-weight: 400;
        text-transform: lowercase;
        font-size: var(--text_s);
        color:  white;
        padding-right: 10px;      
        
    }

</style>