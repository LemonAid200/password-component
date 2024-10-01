<template>
  <div class="password">
    <div class="password_header">
      <button @click="goBack" class="password_header__btn">
        <arrowIcon :color="btnIconsColor"/>
        Back
      </button>
      <h2><b>Password</b></h2>
    </div>

    <CustomInput v-model="password"/>

    <div class="password_buttons">
      <button v-for="i in 9" @click="passwordConcat(i)" class="password_buttons__btn" :key="i">
        {{ i }}
      </button>
      <button @click="passwordClear" class="password_buttons__btn">
        <crossIcon :color="btnIconsColor"/>
      </button>      
      <button @click="passwordConcat(0)" class="password_buttons__btn">
        0
      </button>      
      <button @click="passwordBackspace" class="password_buttons__btn">
        <backspaceIcon :color="btnIconsColor"/>
      </button>
    </div>

    <button @click="passwordSubmit" class="password_continue">
      Continue
    </button>
  </div>
</template>

<script>
import arrowIcon from './icons/arrowIcon.vue'
import backspaceIcon from './icons/backspaceIcon.vue'
import crossIcon from './icons/crossIcon.vue'
import CustomInput from './CustomInput.vue';

export default {
  name: 'PasswordComponent',
  components: {
    arrowIcon,
    backspaceIcon,
    crossIcon,
    CustomInput
  },

  methods: {
    goBack(){
      window.history.back();
    },
    passwordConcat(i){
      if (this.password.length <= 11) this.password +=i
    },
    passwordClear(){
      this.password = ''
    },
    passwordBackspace(){
      this.password = this.password.slice(0, this.password.length - 1)
    },
    passwordSubmit(){
      if (this.password){
        alert('Пароль прошел проверку')
      } else {
        alert('Введите пароль')
      }
    }


  },

  data() {
    return {
      btnIconsColor: '#4E46B4',
      arrowIconColor: 'black',
      password: ''
    }    
  }
}
</script>

<style scoped lang="scss">
// colors
$background: #F6F8FF;  //     Основной фон - #F6F8FF
$purple: #4E46B4;      //    Текст кнопки Back - #4E46B4 Текст кнопок 1…0 - #4E46B4 
$blue: #3448F0;        //   Фон кнопки Continue - #3448F0
$grey: #595D62;        //  Enter admin password - #595D62

button {
  cursor: pointer;
  border: none;
  background: none;
  -webkit-tap-highlight-color: transparent;

  &:focus-visible{
      outline: none;
  }
}


.password {
  max-width: 400px;
  box-sizing: border-box;
  margin: 0 auto;
  background-color: $background;
  padding: 10px;


  &_header {
    display: grid;
    grid-template-columns: 1fr 200px 1fr;

    &__btn {
      color: $purple;
      display: flex;
      align-items: center;
      gap: 8px;

      svg {
        height: 16px;
      }

    }
  }

  &_buttons {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-auto-rows: 90px;
    gap: 8px;
    margin-top: 16px;

    &__btn {
      background: white;
      border-radius: 30px;
      color: $purple;
      font-size: x-large;


      @media (hover:hover){
          &:hover {
              background-color: #4d46b449;
          }
      }

      @media (hover:none) {
          &:active {
              background-color: #4d46b449;
          }                            
      }

    }
  }

  &_continue {
    background-color: $blue;
    color: white;
    font-size: x-large;
    border-radius: 30px;
    width: 100%;
    height: 110px;
    margin-top: 8px;

    &:hover{
      background-color: #172ce9;
    }
  }
}

</style>
