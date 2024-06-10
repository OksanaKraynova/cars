<template>
  <header class="header flex">
    <div class="header-wrapper flex">
        <Menu />
       <div class="header-logo flex">
            <a href="/" class="logo-link">Vechicles</a>
            <div class="counter flex">20</div>
        </div>
        <div class="header-block flex">
            <button class="plus">
                <img  src="/icons/plus.svg" alt="">
            </button>
            <a class="user-block flex">
                <img src="/icons/Photo.jpg" alt="">
                <span>John Doe</span>
            </a>
            <div class="language-block flex">
                <img src="/icons/uk.png" alt="">
               <button class="language-btn flex">
                <span>En</span>
                <img class="img-lan" src="/icons/Vector.svg" alt="">
               </button>
            </div>
        </div>
    </div>
  </header>
</template>

<script>
import Menu from '../components/Menu.vue'
export default {
    components: {
    Menu
  },
}
</script>

<style>
    .header{
        border-bottom: 1px solid rgb(228, 228, 228);
        height: 101px;      
    }
    .header-wrapper{
        padding: 0px 30px;
        justify-content: space-between;
     flex: 1;
     align-items: center;
    }
  
    .header-logo{
        align-items: center;
    }
    .logo-link{
        font-size: 32px;
font-weight: 700;
line-height: 38px;
    }
    .counter{
        margin-left: 18px;
font-weight: 700;
border-radius: 6px;
align-items: center;
justify-content: center;
background: rgb(243, 246, 248);
width: 56px;
height: 30px;
    }
    .user-block{
        align-items: center;
        gap: 14px;
        margin: 0 32px;
    }
    .language-block{
        align-items: center;
    }
    .plus{
        border: 1px solid rgb(232, 110, 132);
        border-radius: 6px;
        width: 42px;
        height: 42px;
        transition: border .3s ease;
    }
    .plus:hover{
        border: 1px solid rgb(217, 14, 50);
    }
    .language-btn{
        margin-left: 15px;
        gap: 11px;
        align-items: center;
    }
    .img-lan{
        transform: rotate(90deg);
    }
  
   @media(max-width: 1098px){
    .header-wrapper{
        justify-content: flex-start;
        
    }
.header-block{
    margin-left: auto;
}
   }
   @media(max-width: 768px){
    .plus, .language-block{
        display: none;
    }
    .header-wrapper{
        padding: 0 15px;
    }
    .logo-link{
        font-size: 24px;
    }
    .counter{
        display: none;
    }
    .header-icon{
        width: 30px;
        height: 30px;
    }
    .user-block{
        margin: 0;
    }
   }
</style>