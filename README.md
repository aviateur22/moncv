# Curriculum vitae
***

## Project presentation

This is a curriculum vitae developped with VueJs.

![image extrait de mon CV](https://github.com/aviateur22/moncv/blob/master/src/assets/images/github/banner.PNG "Titre, facultatif")

## Main feature
- Responsive for **MOBILE** and **TABLET**
- You can present up to 4 projects
- Show your profile picture
- Add your contact

## Changing data

**I will update my code to make it easier.**

- ### Update animation Word
    go to the following file:

>**..\src\components\navigation\BackgroundAnimation.vue** 

>- replace '---' with your own word
> - you can add other object in array with the same structure

     `data(){
        return{
            data:[
                {
                    "darkWord":"---",
                    "colorWord" :"---",
                    "array":["---","---","----"]
                }...
            ]`

- ### changing my profile picture
go to the following file:

>**..src\components\MyDescription.vue** 

> - find and replace '---' with your own URL picture
>
> - image have to be upload in github folder
    
    `<img src='---.png' alt="my beautiful picture" class="profil__img">`




- ### updated project

go to the following file:

>**..src\components\Project.vue** 

> - find and update the PROJECTS array with your own image name and information
> - image have to be upload in github folder

        `projects:[
                        {
                        id:0,
                        date:'2015',
                        name:"poject",
                        technos:['C#','microsoft office'],
                        imgs:[
                                {
                                    id:1,
                                    imgName: 'name of the image.png',
                                    alt:'--description of the image--' 
                                },
                                {
                                    id:2,
                                    imgName: 'name of the image.png',
                                    alt:'--description of the image--' 
                                }
                            ],
                        comments:[
                            'Great job',
                            'Hard time to complete this'
                        ]
                        }`

- ### modified contact

go to the following file:

>**C:\Programmation\moncv\src\components\Contact.vue**

> - update the telefon number 
> - update the email

    `<div class="contact-container">
          <section class="contact">
                <h4><a href="tel:xx xx xx xx xx" class="contact__content">xx xx xx xx xx</a></h4>
          <h5></h5>
      </section>
      <section class="contact contact--mail">            
            <h4><a href="mailto:xxxxxxxx" class="contact__content contact__content--mail">xxxxxxxx</a></h4>
      </section>
    `
