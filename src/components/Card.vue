<template>
   <div class="card">
            <button class="card-more">
                <img src="/icons/more_horizontal.svg" alt="">
            </button>
            <div class="card-image flex">
                <img class="card-img"  :src="card.preview" alt="">
            </div>
            <div class="card-desc">
                <span class="card-name">{{card.vehicle_name}}</span>
                <span class="card-vin"> {{ card.vin }}</span>
            </div>
            <div class="card-footer flex">
                <div class="card-label flex">
                    <img class="label-img"  src="/Vector.svg" alt="">
                    <span>30/30</span>
                </div>
                <div class="card-time">{{new Date(card.created_at * 1000).toLocaleString('ru-RU', { year: 'numeric', month: 'numeric', day: 'numeric' })}}</div>
            </div>
        </div>
</template>

<script>
export default {
    props: {
        card: {
            type: Object,
            required: true
        }
    }
}
</script>

<style>
.card{
        flex: 0 0 354px;
        height: 335px;
        background: rgb(243, 246, 248);
        border-radius: 10px;
        position: relative;
        padding: 40px 0px 38px 0px;
    }
    .card-more{
        position: absolute;
        top: 20px;
        right: 20px;
    }
    .card-image{
        width: 260px;
    height: 135px;
    margin: auto;
    background-color: #E4E4E4;
    }
  
    .card-img{
        object-fit: cover;
        width: 100%;
        max-width: 100%;
        max-height: 100%;
    }
    .card-desc{
        margin-top: 24px;
        display: flex;
        flex-direction: column;
        gap: 12px;
        padding: 0 24px;
    }
    .card-name{
        font-size: 20px;
font-weight: 700;
    }
    .card-vin{
        color: rgba(41, 49, 72, 0.6);
        letter-spacing: 0.3px;
    }
    .card-footer{
        margin: 17.5px 24px 0 24px;
        padding-top: 22.5px;
        border-top: 1px solid rgb(228, 228, 228);
        justify-content: space-between;
        align-items: center;
    }
    .card-label{
        width: 93px;
height: 30px;
border-radius: 6px;
background: rgb(228, 245, 221);
align-items: center;
justify-content: center;
color: rgb(127, 199, 94);
font-weight: 700;
gap: 7.5px;
    }
    .label-img{
        width: 16px;
height: 16px;
    }
    .card-time{
        color: rgba(41, 49, 72, 0.6);
    }
</style>