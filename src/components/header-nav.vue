<template>
<header class="header">
  <a href="" class="header__logo">
    <p class="header__logo-text">LOGO</p>
  </a>
  <nav class="header__nav">
    <ul class="header__nav-list">
      <li class="header__nav-item">
        <a href=""><p>How it works</p></a>
      </li>
      <li class="header__nav-item">
        <a href=""><p>About</p></a>
      </li>
      <li class="header__nav-item">
        <a href=""><p>Instructions</p></a>
      </li>
      <li class="header__nav-item">
        <a href=""><p>Accounts</p></a>
      </li>
      <li class="header__nav-item">
        <a href=""><p>Platforms</p></a>
      </li>
      <li class="header__nav-item">
        <a href=""><p>Contact</p></a>
      </li>
    </ul>
  </nav>
  <div class="header__menuMob">
    <img @click="openMenu" src="../assets/eva_menu-fill.svg" alt="Burger menu icon">
    <div v-if="showMenu" class="header__menuMob-menu">
      <nav class="header__navMob">
        <ul class="header__navMob-listMob">
          <li class="header__navMob-itemMob">
            <p>How it works</p>
          </li>
          <li class="header__navMob-itemMob">
            <p>About</p>
          </li>
          <li class="header__navMob-itemMob">
            <p>Instructions</p>
          </li>
          <li class="header__navMob-itemMob">
            <p>Accounts</p>
          </li>
          <li class="header__navMob-itemMob">
            <p>Platforms</p>
          </li>
          <li class="header__navMob-itemMob">
            <p>Contact</p>
          </li>
          <li class="header__mob">
            <div class="header__signMob">
              <button>
                <p>Sign in for free</p>
              </button>
            </div>
          </li>
          <li>
            <div class="header__selectMob" @click="openLangsMob">
              <p>{{selectedLang}}</p>
              <img src="../assets/Vector.svg" alt="Vector">
              <div v-if="openLangMob" class="header__dropDownMob">
                <p v-for="item in langs" :key="item" @click="selectLang(item)">
                  {{item}}
                </p>
              </div>
            </div>
          </li>
        </ul>
      </nav>
    </div>
  </div>
  <div class="header__sign">
    <button id="button_sign">
      <p>Sign in for free</p>
    </button>
  </div>
  <div class="header__select" @click="openLangs">
    <p>{{selectedLang}}</p>
    <img src="../assets/Vector.svg" alt="Vector">
    <div v-if="openLang" class="header__dropDown">
      <p v-for="item in langs" :key="item" @click="selectLang(item)">
        {{item}}
      </p>
    </div>
  </div>



</header>
</template>

<script>
export default {
name: "header-nav",
  data(){
  return{
    showMenu:false,
    openLang:false,
    openLangMob:false,
    selectedLang: 'UA',
    langs:['EN', 'RU', 'UA']
  }
  },
  methods: {
  selectLang(lang){
    this.selectedLang = lang;
  },
  openLangs(){
    this.openLang = !this.openLang;
    this.showMenu ? this.showMenu = !this.showMenu: '';

  },
    openMenu(){
      this.showMenu = !this.showMenu;
      this.openLang ? this.openLang = !this.openLang : '';
      this.openLangMob ? this.openLangMob = !this.openLangMob: '';
    },
    openLangsMob(){
      this.openLangMob = !this.openLangMob;
    }
  }

}
</script>

<style scoped lang="scss">
.header{
  width: 100%;
  height: 80px;
  background-color: #FFFFFF;
  &__logo{
    float: left;
    margin-top: 32px;
    margin-left: 120px;
    &-text{
      font-style: normal;
      font-weight: bold;
      font-size: 15px;
      line-height: 16px;
      color: #333333;
    }
  }
  &__navMob{

    &-listMob{
      //display: block;
      list-style: none;
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: flex-end;
      li{
        //margin-top: 10px;
        //padding: 5px;
        width: 100%;
        padding: 10px 0px;
        p{
          margin-left: 10px;
        }
      }
      li:hover{
        background-color: #828282;
      }

    }
  }
  &__menuMob{
    float: right;
    margin-top: 32px;
    margin-right: 28px;
    display: none;
    &-menu{
      position: absolute;
      right: 0px;
      width: 100%;
      background: #bcb2fa;
      border-radius: 10px;
      //width: 200px;
      margin-top: 20px;
      //height: 100vh;
    }
  }
  &__nav{
    float: left;
    margin-left: 57px;
    margin-top: 32px;
    &-list{
      display: flex;
      list-style: none;
      padding: 0;
      margin: 0;
    }
    &-item{
      margin-left: 32px;
    }
    //&-item:hover{
    //  cursor: pointer;
    //}
    &-item:first-child{
      margin-left: 0;
    }
  }
  &__select{
    float: right;
    width: 80px;
    height: 40px;
    border: 1px solid #000000;
    box-sizing: border-box;
    border-radius: 60px;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    margin-top: 20px;
    margin-right: 24px;
    outline: none;
    p{
      font-style: normal;
      font-weight: 500;
      font-size: 15px;
      line-height: 16px;
      color: #333333;
    }
    img{
      width: 9px;
      height: 5px;
    }
  }
  &__select:hover{
    cursor: pointer;
  }

  &__selectMob{
    //float: right;
    margin-left: 10px;
    width: 80px;
    height: 40px;
    border: 1px solid #000000;
    box-sizing: border-box;
    border-radius: 60px;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    margin-top: 20px;
    margin-right: 24px;
    outline: none;
    p{
      font-style: normal;
      font-weight: 500;
      font-size: 15px;
      line-height: 16px;
      color: #333333;
    }
    img{
      width: 9px;
      height: 5px;
    }
  }
  &__selectMob:hover{
    cursor: pointer;
  }
  &__sign{
    button {
      float: right;
      padding: 13px 24px;
      width: 167px;
      height: 40px;
      background: #6248FF;
      border-radius: 60px;
      border: none;
      margin-top: 20px;
      margin-right: 60px;
      transition: 0.5s;
      outline: none;
      p{
        font-style: normal;
        font-weight: 500;
        font-size: 14px;
        line-height: 14px;
        text-transform: uppercase;
        color: #FFFFFF;
      }
    }
    button:hover{
      background: #7181FC;
      cursor: pointer;
    }
    button:active{
      background: #354BF4;
    }

  }
  &__signMob{
    button {
      padding: 13px 24px;
      width: 187px;
      height: 45px;
      background: #6248FF;
      border-radius: 60px;
      border: none;
      margin-top: 20px;
      margin-right: 60px;
      transition: 0.5s;
      outline: none;
      margin-left: 10px;
      p{
        font-style: normal;
        font-weight: 500;
        font-size: 14px;
        line-height: 14px;
        text-transform: uppercase;
        color: #FFFFFF;
      }
    }
    button:hover{
      background: #7181FC;
      cursor: pointer;
    }
    button:active{
      background: #354BF4;
    }

  }
  &__dropDown{
    position: absolute;
    margin-top: 200px;
    background: #bcb2fa;
    width: 100px;
    display: flex;
    flex-direction: column;
    align-items: center;
    P{
      width: 100%;
      height: 20px;
      text-align: center;
      padding: 10px;
    }
    p:hover{
      background-color: #828282;
      cursor: pointer;
    }
  }
  &__dropDownMob{
    position: absolute;
    margin-top: 180px;
    background: #bcb2fa;
    width: 100px;
    display: flex;
    flex-direction: column;
    align-items: center;
    P{
      width: 100%;
      height: 20px;
      text-align: center;
      padding: 10px;
    }
    p:hover{
      background-color: #828282;
      cursor: pointer;
    }
  }
  &__mob{
    display: none;
  }
}
@media screen and (max-width:1155px) {
  .header{
    &__logo{
      margin-left: 60px;
    }
  }
}

@media screen and (max-width:1100px) {
.header{
  &__nav{
    display: none;
  }
  &__menuMob{
    display: block;
  }
  &__select{
    display: none;
  }
}
}

@media screen and (max-width: 540px){
  .header{
    &__sign{
      display: none;
    }
    &__mob{
      display: block;
    }
  }
}
</style>
