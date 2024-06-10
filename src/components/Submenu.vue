<template>
  <aside class="submenu">
    <div class="sub-title">Demo Test</div>
    <ul class='sub-list'>
        <li  v-for="link in links" :key="link.name">
            <a class="sub-link" href="">
                <img :src="link.img" alt="">
                <span>{{link.name}}</span>
            </a>
        </li>
    </ul>
  </aside>
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
    ]
    }
}
}
</script>

<style>
    .submenu{
        width: 256px;
        background: url(../../background.png) ;
        display: flex;
        flex-direction: column;
        min-height: 100vh;
        color: #fff;
        padding-top: 30px;
    }
    .sub-title{
        font-size: 24px;
        font-weight: 700;
        text-align: center;
    }
    .sub-list{
        margin-top: 102px;
        display: flex;
        flex-direction: column;
        gap: 16px;
    }
    .sub-link{
height: 48px;
display: flex;
padding-left: 33px;
align-items: center;
font-size: 16px;
gap: 23px;
transition: background 0.3s ease;
    }
    .sub-link:hover{
        background: rgba(255, 255, 255, 0.1);
    }
    .sub-link.active{
background: rgba(255, 255, 255, 0.2);
    }
@media(max-width: 1098px){
    .submenu{
        display: none;
    }
}
</style>