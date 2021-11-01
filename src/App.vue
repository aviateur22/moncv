<template>
  <div class="container">
    <Navigation/>
    <MyDescription/>
    <ProfessionnalExperience/>
    <Techno/>
    <Project :projects="projects"/>
    <Contact/>
    <FooterLinkedin/>
  </div>
  
</template>

<script>
import Navigation from './components/NavBar.vue';
import MyDescription from './components/MyDescription.vue';
import ProfessionnalExperience from './components/ProfessionalExcperience.vue';
import Techno from './components/Techno.vue';
import Contact from './components/Contact.vue';
import Project from './components/Project.vue';
import FooterLinkedin from './components/FooterLinkedin.vue';


export default {
  name: 'App',
  components: {
    Navigation,
    MyDescription,
    ProfessionnalExperience,
    Techno,
    Project,
    Contact,
    FooterLinkedin
  }, 
  data(){
    return{
      /**
       * Data pour les présentations de projet
       */

     projects:[
                    {
                        id:0,
                        date:'2015',
                        name:"easylux",
                        technos:['C#','microsoft office'],
                        imgs:[
                            {
                                id:1,
                                imgName: 'projet1-1.png',
                                alt:'premiere photo de easylux v1' 
                                },
                               {
                                   id:2,
                                   imgName: 'projet1-2.png',
                                   alt:'seconde photo de easylux v1' 
                               }
                        ],
                        comments:[
                            'études problématiques dans notre travail',
                            'proposition et conception d\'un logiciel sur mesure'
                        ]
                    },
                     {
                        id:2,
                        date:'2016',
                        name:"notam manager v1",
                        technos:[ 'C#','microsoft office','requète API'],
                        imgs:[
                                {
                                    id:1,
                                    imgName: 'projet2-1.png',
                                    alt:'premiere photo de notam manager v1' 
                                },
                                {
                                    id:2,
                                   imgName: 'projet2-2.png',
                                   alt:'seconde photo de notam manager v1' 
                                }
                            ],
                        comments:['proposition logiciel pour suivre les notams d\'un aéroport','utilisation de la librairie GMAP',]
                    },
                    {
                        id:1,
                        date:'2018',
                        name:"easylux v2",
                        technos:['C# WPF' ,'requète API','sqlite'],
                        imgs:[
                                {
                                    id:1,
                                    imgName: 'projet3-1.png',
                                    alt:'premiere photo de easylux v2' 
                                },
                               {
                                   id:2,
                                   imgName: 'projet3-2.png',
                                   alt:'seconde photo de easylux v2' 
                               },
                               {
                                    id:3,
                                    imgName: 'projet3-3.png',
                                    alt:'troisieme photo de easylux v2' 
                                },
                               {
                                   id:4,
                                   imgName: 'projet3-4.png',
                                   alt:'quatrieme photo de easylux v2' 
                               }
                            ],
                        comments:['enquête sur les besoins d\'amélioration','etablissement cahier des charges','wireframe sur figma','integration de Bigmap']
                    },                   
                    {
                        id:3,
                        date:'2020',
                        name:"notam manager v2",
                        technos:['Google Apps Script','javascript','requète API'],
                        imgs:[
                                {
                                    id:1,
                                    imgName: 'projet4-1.png',
                                    alt:'premiere photo de notam manager v2' 
                                },
                                {
                                    id:2,
                                   imgName: 'projet4-2.png',
                                   alt:'seconde photo de notam manager v2' 
                                },
                                {
                                    id:3,
                                   imgName: 'projet4-3.png',
                                   alt:'troisieme photo de notam manager v2' 
                                }
                            ],
                        comments:['proposition d\'une évolution suite a la disparaition de m.office','enquête sur les besoins','etablissement cahier des charges','wireframe et prototyping sur figma','connexion a google drive','gestion du responsive'],
                    }
            ],
    }
  },
 
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

html, body {
  font-family: 'Roboto', sans-serif;
  scroll-behavior: smooth;
}
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}


</style>
