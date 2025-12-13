<template>
  <div>
    <h1 class="title">yadon</h1>
    <div class="wrap wrap1">
        <p>漸層方塊</p>
        <div class="color_box"></div>
        <hr>
    </div>
    <div class="wrap wrap2">
        <p>自製下拉</p>
        <button class="color_box" type="button" @click="menuHandler()">
            <p class="item_title">棟別</p>
            <p class="item_name">{{ '陶朱隱園' }}</p>
            <img class="arrow" src="@/assets/down.png" alt="">
        </button>
        <!-- <div class="menu_out" v-if="filterStatus.Tower">
            <div class="menu_in">
                <a href="#" class="item">陶朱隱園</a>
                <a href="#" class="item">都廳大院</a>
                <a href="#" class="item">國王大道</a>
                <a href="#" class="item">文華苑</a>
                <a href="#" class="item">甲山林濱河帝景</a>
                <a href="#" class="item">遠揚之森</a>
                <a href="#" class="item">寶亞鴻公舘</a>
                <a href="#" class="item">協和新中興</a>
            </div>
        </div> -->
        <div class="menu" v-if="filterStatus.Tower" :class="{menu_true: filterStatus.Tower}">
            <a href="#" class="item">陶朱隱園</a>
                <a href="#" class="item">都廳大院</a>
                <a href="#" class="item">國王大道</a>
                <a href="#" class="item">文華苑</a>
                <a href="#" class="item">甲山林濱河帝景</a>
                <a href="#" class="item">遠揚之森</a>
                <a href="#" class="item">寶亞鴻公舘</a>
                <a href="#" class="item">協和新中興</a>
        </div>
        <!-- <hr> -->
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
            Floor: 0,
            Area: 0
        }
    }
  },
  
  methods:{
    test() {
        alert('123')
    },
    menuHandler() {
        this.filterStatus.Tower = !this.filterStatus.Tower;
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

    .wrap2{
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
            height: 0;
            background: linear-gradient(135deg, #1572ff, #334f76);
            overflow: hidden;
            transition: 1s;

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
            height: 500px;
        }
        .menu_false{
            height: 0;
        }
        // =========================
        .menu_out{
            position: relative;
            width: 330px;
            height: 500px;
            background: linear-gradient(135deg, #1572ff, #334f76);
            overflow: hidden;
            animation: menu_opacity 1s;
            transition: 1s;
            .menu_in{
                position: absolute;
                width: 330px;
                height: 500px;
                top: -5px; // 動畫改變化這個
                animation: menu_move .5s ease-in;
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
        }
        
    }

    @keyframes menu_opacity {
        0%{
            opacity: 0;
        }

        100%{
            opacity: 1;
        }
    }
    @keyframes menu_move {
        0%{
            top: -100%;
        }

        100%{
            top: -5px
        }
    }
    @keyframes menu_length {
        0%{
            height: 0;
        }

        100%{
            height: 500px;
        }
    }
</style>
