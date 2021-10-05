<template>
  <div class="mobile-menu" :class="{'display-mobile-menu': this.data }">
        <!-- menu close -->
       
        <section @click="emitToggleMobileMenu" class="close-btn">
            <div class="close-btn__line1"></div>            
            <div class="close-btn__line2"></div>
        </section>
    </div>   
</template>

<script>
export default {
    name:'MobileNavigation',
    data(){
        return{
            
        }
    },
    props:['data'],
    methods:{
        emitToggleMobileMenu(){
            // renvoie false pour l'affichage de l'overlay
            this.$emit('updateMobileMenudata', false)
        }
    }

}
</script>

<style>

    .display-mobile-menu{
        display: block !important;
    }
    .mobile-menu{
        display: none;
        position: fixed;
        left: 0px;
        top:0px;
        bottom: 0px;
        right: 0px;
        background-color: rgba(0, 0, 0, 0.8);
        z-index: 2;
    }


    .close-btn{
        margin: 25px;
        position: absolute;        
        cursor: pointer;        
        right: 0px;        
        top: 0px;
        overflow: hidden;
        padding:20px 0 0;
        transform: translate(-50%, -50%);
        transition: all 0.2s ease-in;
        width: 20px;

    }

    .close-btn::before,
    .close-btn::after {
        background-color: white;
        content: '';
        display: block;
        height: 2px;
        left: 0;
        position: absolute;
        transform-origin: center left;
        transition: all 0.2s ease-in;
        width: 50px;
        z-index: -1;
    }

    .close-btn::before {
    top: 0;
    transform: rotate(45deg);
    }

    .close-btn::after {
    bottom: 1;
    transform: rotate(-45deg);
    }

    .close-btn:hover::after,
    .close-btn:hover::before
    {
        height: 2.5px;

    }

</style>