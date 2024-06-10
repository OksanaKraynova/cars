<template>
  <nav class="burger">
    <transition name="fade" mode="out-in" >
<img class="header-icon" src="/icons/menu.svg" v-if="!show" @click="show = !show " key="menu" alt="">
<img class="header-icon" src="/icons/close.png" v-else @click="show = !show" key="close" alt="">
    </transition>
    <transition>
        <ul class="mobile-list" v-if="show"  >
                <li class="mobile-item" v-for="link in links" :key="link.name">
                    <a href="" class="mobile-link">
                    <img :src="link.img" alt="">
                <span>{{ link.name }}</span>
                </a>
            </li>
                
            </ul>
    </transition>
</nav> 
</template>

<script>
export default {
    data(){
    return{
        links: [
        {
            name: 'Profile',
            img:'/icons/user.svg'
        },
        {
            name: 'Vechicles',
            img:'/icons/rim.svg'
        },
        {
            name: 'Settings',
            img:'/icons/settings.svg'
        },
    ],
    show: false
    }
    }
}
</script>

<style>
  .burger{display: none;}
  .header-icon{
        width: 50px;
        height: 50px;
    }
 @media(max-width: 1098px){
       .burger{
        display: block;
    margin-right: 14px;
}
.mobile-list{
position: absolute;
font-size: 20px;
background-color: #212121;
color: #fff;
left: 0;
width: 320px;
height: 130px;
top: 82px;
z-index: 99999px;
}
.mobile-link{
    display: flex;
    align-items: center;gap: 14px;
    height: 34px;
padding: 10px 30px;
}
.mobile-item{
    height: 34px;
    padding: 10px 0;
}
   }
</style>