<template>
  <div class="main">
    <div class="main-row flex">
        <div class="input-wrapper flex">
            <input v-model='search' type="text" name="" id="" placeholder="Search VIN">
            <img src="/icons/zoom.svg" alt="">
        </div>
        <div class="select-block flex">
            <span>Select vehicles per page</span>
            <select v-model="limit" >
              <option  value="9" >9</option>
              <option value="18">18</option>
            </select>
           
        </div>
        <div class="add-block">
            <button class="add-btn flex">
                <img src="/icons/plus2.svg" alt="">
                <span>ADD VECHICLE</span>
            </button>
        </div>
    </div>
    <cards :cards='searchCards'  v-if='!isLoading' />
    <div class="loading" v-else >Загрузка...</div>
    <div class="pages-wrapper flex">
        <div class="pages-desc">Showing {{ searchCards.length }} out 20</div>
        <div class="pages-block flex">
<button  @click="prevPage" :disabled='page == 1'>
                <img src="/icons/chevron_left.svg" alt="">
            </button>
            <div class='pages-num flex' v-for='p in totalPages' :class='{"current": page === p}'  :key='p' @click='changePage(p)' >{{p}}</div>
            <button @click="nextPage" :disabled="page == 3">
                <img class="rotate" src="/icons/chevron_left.svg" alt="">
            </button>
        </div>
            
            
    </div>
  </div>
</template>

<script>
import Cards from '../components/Cards.vue';
import axios from 'axios'
export default {
    components: {
    Cards
  },
    data() {
    return {
      cards: [],
      isLoading: false,
      search: '',
      page: 1,
      limit: 9,
      totalPages: 0
    }
  },
  
  methods: {
    async getCards(){
      try{
        this.isLoading = true
          const res = await axios.get(`https://api.caiman-app.de/api/cars-test?search=${this.search}&per_page=${this.limit}&page=${this.page}`)
          console.log(res);
          this.totalPages = Math.ceil(20 / this.limit)
          this.cards = res.data.data
        
        } catch(e){
          alert('Ошибка')
        } finally{
        this.isLoading = false
        }
     
    },
      changePage(num) {
    this.page = num
    this.getCards()
    },
    nextPage(){
         this.page++;
         this.getCards()
      },
      prevPage(){
        this.page--;
        this.getCards()
      },
  },
  mounted(){
    this.getCards()
  },
  computed: {
    searchCards(){
      return this.cards.filter(post => post.vin.toLowerCase().includes(this.search.toLowerCase()))
    },
  
  }
}
</script>

<style>
.main{
    padding: 36px 30px 49px 30px;
}
.main-row{
    gap: 32px;
}
.input-wrapper{
    width: 354px;
    height: 42px;
    padding: 9px 11px 9px 16px;
    border: 1px solid rgb(228, 228, 228);
border-radius: 8px;
}
input{
    flex: 1;
}
input:focus .input-wrapper{
    border: 1px solid rgb(120, 149, 255);
}
    .select-img{
        transform: rotate(90deg);
    }
    .select-block{
        font-size: 16px;
font-weight: 400;
align-items: center;
gap: 16px;
    }
    select{
      border: 1px solid rgb(228, 228, 228);
    border-radius: 8px;
    width: 85px;
    height: 42px;
    font-size: 16px;
    font-weight: 400;
    align-items: center;
    justify-content: center;
    padding: 0 15px;
    gap: 18px;
    }
    .add-block{
        margin-left: auto;
    }
    .add-btn{
        box-shadow: 0px 8px 24px 0px rgba(217, 14, 50, 0.12);
        background: rgb(217, 14, 50);
        width: 180px;
        height: 42px;
        border-radius: 10px;
        align-items: center;
        justify-content: center;
        color: rgb(255, 255, 255);
        font-size: 12px;
font-weight: 700;
letter-spacing: 1px;
gap: 14px;
transition: all .3s ease;
    }
    .add-btn:hover{
        box-shadow: 0px 8px 24px 0px rgba(217, 14, 50, 0.07);
background: rgba(217, 14, 50, 0.85);
    }
   
    .pages-wrapper{
        padding-top: 36px;
        justify-content: space-between;
        align-items: center;
    }
    .pages-desc{
        color: rgba(41, 49, 72, 0.8);
font-size: 16px;
font-weight: 400;
    }
    .pages-block{
        align-items: center;
        gap: 15px;
    }
    .pages-num{
        width: 32px;
        height: 32px;
        border-radius: 6px;
        border: 1px solid #E4E4E4;
        color: #E4E4E4;
        align-items: center;
        justify-content: center;
        cursor: pointer;
    }
    .loading{
      margin-top: 30px;
      text-align: center;
      font-size: 16px;
    }
    .rotate{
        transform: rotate(180deg);
    } 
    .current{
      color:  #293148CC ;
    }
    @media(max-width: 998px){
.select-block{
  display: none;
}
.main-row{
  gap: 24px;
}
.add-block{
  margin: 0;
}
    }
    @media(max-width: 768px){
      .main-row{
        flex-direction: column;
      }
      .add-block{
 width: 100%;
}
.add-btn, .input-wrapper{
 flex: 1;
 width: 100%;
}
.pages-desc{
display: none;
}
.pages-wrapper{
justify-content: center;
}
    }
</style>