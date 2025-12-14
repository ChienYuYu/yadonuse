<template>
  <div @click="closeAllFilters()">
    <h1 class="title">yadon</h1>
    <div class="wrap wrap1">
        <p>漸層方塊</p>
        <div class="color_box"></div>
        <hr>
    </div>
    <div class="wrap wrap2">
        <p>自製下拉</p>
        <button class="color_box" type="button" @click.stop="menuHandler('tower')">
            <p class="item_title">棟別</p>
            <p class="item_name">{{ '陶朱隱園' }}</p>
            <img class="arrow" src="@/assets/down.png" alt="">
        </button>
        <div class="menu" :class="{menu_true:filterStatus.Tower}">
            <a href="#" class="item">陶朱隱園</a>
            <a href="#" class="item">都廳大院</a>
            <a href="#" class="item">國王大道</a>
            <a href="#" class="item">文華苑</a>
            <a href="#" class="item">甲山林濱河帝景</a>
            <a href="#" class="item">遠揚之森</a>
            <a href="#" class="item">寶亞鴻公舘</a>
            <a href="#" class="item">協和新中興</a>
        </div>
        <hr>
    </div>
    <div class="wrap wrap3">
        <button class="color_box" type="button" @click.stop="menuHandler('floor')">
            <p class="item_title">棟別</p>
            <p class="item_name">{{ '87F' }}</p>
            <img class="arrow" src="@/assets/down.png" alt="">
        </button>
        <div class="menu" :class="{menu_true:filterStatus.Floor}">
            <a href="#" class="item">87F</a>
            <a href="#" class="item">88F</a>
            <a href="#" class="item">89F</a>
        </div>
        <hr>
    </div>
    <div class="wrap wrap4">
        <label>
            <input type="radio" id="elc" name="group1">
            <p>相電壓</p>
        </label>
        <label>
            <input type="radio" id="elc" name="group1">
            <p>線電壓</p>
        </label>
        <label>
            <input type="radio" id="elc" name="group1">
            <p>相電流</p>
        </label>
        <label>
            <input type="radio" id="elc" name="group1">
            <p>有效功率</p>
        </label>
        <label>
            <input type="radio" id="elc" name="group1">
            <p>無效功率</p>
        </label>
    </div>
  </div>
</template>

<script>

export default {
  name: 'YaDon',
  created() {},
  mounted() {},
  data() {
    return {
        filterStatus:{
            Tower: false,
            Floor: false,
            Area: false
        }
    }
  },
  
  methods:{
    
    menuHandler(type) {
        if(type === 'tower') {
            this.filterStatus.Tower = !this.filterStatus.Tower;
            this.filterStatus.Floor = false;
        }
        if(type === 'floor') {
            this.filterStatus.Floor = !this.filterStatus.Floor;
            this.filterStatus.Tower = false;
        }
        
    },

    closeAllFilters() {
        this.filterStatus.Tower = false;
        this.filterStatus.Floor = false; 
        this.filterStatus.Area = false;
    }
  }
}
</script>

<style lang="scss">
    h1.title{
        text-align: center;
        font-size: 30px;
    }

    .wrap{
        div.color_box{
            width: 300px;
            height: 100px;
            background: #000;
            background: linear-gradient(135deg, #1572ff, #334f76);
        }
    }

    .wrap, .wrap3{
        button.color_box{
            position: relative;
            z-index: 10;
            border: none;
            box-shadow: 0 4px 4px #154082;
            width: 330px;
            height: 85px;
            background: #000;
            border-radius: 10px;
            background: linear-gradient(135deg, #1572ff, #334f76);

            p{
                font-size: 22px;
                position: absolute;
            }
            p.item_title{
                top: 10px;
                left: 15px;
                color: #fff;
            }

            p.item_name{
                color: #83c3ff;
                bottom: 10px;
                right: 15px;
            }
            img.arrow{
                position: absolute;
                right: 15px;
                top: 10px;
            }
        }
        .menu{
            position: relative;
            width: 330px;
            background: linear-gradient(135deg, #1572ff, #334f76);
            overflow: auto;
            transition: .5s;
            height: 0px;

            /* WebKit 滾動條樣式 */

            /* 整個滾動條的寬度/高度 */
            &::-webkit-scrollbar {
                width: 10px; /* 垂直滾動條的寬度 */
                height: 10px; /* 水平滾動條的高度 */
            }
        
            /* 滾動條的軌道（背景） */
            &::-webkit-scrollbar-track {
                background: #254F7F00; /* 您的漸層底色附近，或者透明 */
                border-radius: 5px;
            }
        
            /* 滾動條的拉柄 (Thumb) */
            &::-webkit-scrollbar-thumb {
                background: #83C3FF; /* 亮色系，與漸層背景 #1572ff 搭配 */
                background: #d9d9d9; 
                border-radius: 5px;
                /* 可選：讓拉柄在軌道中有邊距，避免緊貼邊緣 */
                border: 2px solid #254F7F; 
            }
        
            /* 懸停時的拉柄顏色 */
            &::-webkit-scrollbar-thumb:hover {
                background: #fff;
            }

            a.item{
                font-size: 2.5vh;
                display: block;
                text-align: center;
                text-decoration: none;
                color: #fff;
                border-bottom: 1px solid #fff;
                padding: 1rem 0;
                &:hover{
                    background: #83C3FF;
                }
            }
        }
        .menu_true{
            height: 400px;
        }

    }

    .wrap4{
        display: flex;
        label{
            margin: 0 10px;
            padding: 0 .5rem;
            width: 130px;
            height: 40px;
            background: #1572FF;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-radius: 5px;
            input{
                width: 25px;
                height: 25px;
            }
            p{
                font-size: 18px;
                // line-height: 40px;
                color: #fff;
                vertical-align: top;
            }
        }
    }

</style>
