<template>
  <div class="container">
    <Navigation/>
    <MyDescription :myDescription="myDescription"/>
    <ProfessionnalExperience :experiences="experiences"/>
    <Techno/>
    <Project :projects="projects"/>
    <Contact :contact="contact"/>
    <FooterLinkedin :footerData="footerData"/>
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
       * Ma présentation
       */
      myDescription:{
        /**My presentation */
        presentationItem1:'Je suis autodidacte et pationné en développement Web et logiciel depuis quelques années. Aujourd\'hui, je franchis le pas, en commençant une reconversion professionnelle pour devenir développeur Web.  ',
        presentationItem2:'Mon travail actuel m\'a permis d\'acquérir autonomie et le goût d\'être en équipe.\n Mes rèsponsables m\'ont fait confiance et j\'ai ainsi eu l\'occasion de proposer, développer et de mettre en place certains logiciels.',
        presentationItem3: 'Je suis de nature curieuse et j\'aime apprendre. Mon défis actuel est l\'apprentissage de VUEJS.',

        /**Name and First name */
        name:'Cyrille',
        lastName:'Cadé',

        /**date of birth */
        birthday:{
          day:26,
          month:12,
          year:1983
        },

        /**Adress */
        city:'Auterive',
        zipCode:'31190',

        /**Picture */
        myPictureName:'myPicture',
      },

      /**
       * Mon experience - mon parcours
       */
       experiences:[
                {
                    title:"reconversion professionnelle",
                    date:"aujourd'hui à 2021",
                    subTitle:"",
                    items:[
                      'HTML/CSS/Javascript',
'                      React & NodeJS',
                      'modélisation et implémentation de base de données',
                      'Gestion de projet avec la méthodologie AGILE',
                      'Déploiement sur serveur',
                      'réalisation complète d’une application WEB  ',
                    ]
                },
                {
                    title:"autodidacte",
                    date:"2021 à 2013",
                    subTitle:"Pationné par le développement WEB et logiciel:",
                    items:[
                        'Apprentissage de diffrents languages de programmation',
                        'Création d\'applications personnelles',
                        'Test de wireframe et prototype sur figma',
                        'ébauche de projet pour la famille',
                        'développement d\'application pour mon travail'
                    ]

                }
            ],
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
      
      /**
       * Contact mail et phone
       */
      contact:{
        mail:'avaiateur22@hotmail.fr',
        phone: '06 23 27 41 01'
      },

      /**
       * data footer
       */
      footerData:{
        link:'https://www.linkedin.com/in/cyrille-cade-b58323206/',
        footerName: `Cyrille Cadé`,
        footerYear : new Date().getFullYear(),
      },
      
      /**
       *
       */
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
