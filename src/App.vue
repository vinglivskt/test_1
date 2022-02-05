
<template>
  <form @submit.prevent="someAction()">

    <div for="name" style="text-align: center;">Форма регистрации </div>
    <br>


    <!-- Фамилия -->
    <div class="field">
      <label for="name">Фамилия(*)</label>
      <input
          id="surname"
          type="text"
          v-model="surname"
          @blur="$v.surname.$touch()"
      >
      <div class="error" v-if="$v.surname.$error">
        <template v-if="!$v.surname.alpha">
          Фамилия должна содержать только буквы
        </template>
        <template v-else>
          Фамилия обязательна для заполнения
        </template>
      </div>
    </div>


    <!-- Имя-->
    <div class="field">
      <label for="name">Имя(*)</label>
      <input
          id="name"
          type="text"
          v-model="name"
          @blur="$v.name.$touch()"
      >
      <div class="error" v-if="$v.name.$error">
        <template v-if="!$v.name.alpha">
          Имя должно содержать только буквы
        </template>
        <template v-else>
          Имя обязательно для заполнения
        </template>
      </div>
    </div>


    <!-- Отчество -->
    <div class="field">
      <label for="name">Отчество</label>
      <input
          id="patronymic"
          type="text"
          v-model="patronymic"
          @blur="$v.patronymic.$touch()"

      >
      <div class="error" v-if="$v.patronymic.$error">
        <template v-if="!$v.patronymic.alpha" >
          Отчество должно содержать только буквы
        </template>
      </div>
    </div>


    <!-- Дата рождения -->
    <div class="field">
      <label for="name">Дата рождения(*)</label>
      <input
          id="birth_date"
          type="text"
          v-model="birthDate"
          placeholder="ДД.ММ.ГГГГ"
          @blur="$v.birthDate.$touch()"
      >
      <div class="error" v-if="$v.birthDate.$error">
        <template v-if="!$v.birthDate.alpha" >
          Дата рождения обязательна для заполнения в формате: ДД.ММ.ГГГГ
        </template>
      </div>
    </div>


    <!-- Номер телефона -->
    <div class="field">
      <label for="name">Номер телефона(*)</label>
      <input
          id="phone"
          type="text"
          v-model="phone"
          placeholder="+7 (___) ___ __ __"
          @blur="$v.phone.$touch()"
      >
      <div class="error" v-if="$v.phone.$error">
        <template v-if="!$v.phone.maxLength">
          Длина Номера не должна превышать {{ $v.phone.$params.maxLength.max }} символов
        </template>
        <template v-else-if="!$v.phone.alpha">
          Номер телефона должен содержать только цифры и начинаться с +7
        </template>
        <template v-else>
          Номер обязателен для заполнения
        </template>
      </div>
    </div>


    <!-- Пол -->
    <div class="fab-backdrop">
      <label for="name">Выберите пол: </label>
      <input
          type="radio"
          value="M"
          v-model="gender">
      <label>M</label>
      <input
          type="radio"
          value="W"
          v-model="gender">
      <label>Ж</label>
    </div>
    <br>


    <!-- Группа клиентов -->
    <div class="fab-backdrop">
      <label for="name">Группа клиентов(*)</label>
      <div><select  v-model="users" @blur="$v.users.$touch()"  multiple>

        <option>VIP</option>
        <option>Проблемные</option>
        <option>ОМС</option>
      </select>
        <div class="error" v-if="$v.users.$error">
          <template>
            Группа клиентов обязательна для заполнения
          </template>
        </div>
      </div>
      <br>


      <!-- Лечащий врач -->
      <div class="fab-backdrop">
        <label for="name">Лечащий врач</label>
        <div id="app">
          <select v-model="user">
            <option>Иванов</option>
            <option>Захаров</option>
            <option>Чернышева</option>
          </select>
        </div>
      </div>
    </div>
    <br>


    <!-- Не отправлять СМС -->
    <div class="fab-backdrop">
      <label for="name">Не отправлять СМС: </label>
      <input
          type="radio"
          value="Yes"
          v-model="SMS">
      <label>Да</label>
    </div>
    <br>


    <!-- Адрес-->
    <div class="field">
      <div for="name" style="text-align: center;">Адрес</div>
      <br>
      <div class="field">
        <label>Индекс</label>
        <input
            id="ind"
            type="text"
            name="ind"
            v-model="ind"
            @blur="$v.ind.$touch()">

        <div class="error" v-if="$v.ind.$error">
          <template v-if="!$v.ind.alpha">
            Индекс должен содержать только цифры
          </template>
          <template v-else-if="!$v.ind.maxLength">
            Длина Индекса не должна превышать {{ $v.ind.$params.maxLength.max }} символов
          </template>

        </div>
      </div>


      <!-- Страна -->
      <div class="field">
        <label>Страна</label>
        <input
            type="text"
            name="country"
            v-model="country"
            @blur="$v.country.$touch()">
        <div class="error" v-if="$v.country.$error">
          <template v-if="!$v.country.alpha">
            Страна должна содержать только буквы
          </template>
        </div>
      </div>


      <!-- Область-->
      <div class="field">
        <label>Область</label>
        <input
            type="text"
            name="obl"
            v-model="obl"
            @blur="$v.obl.$touch()">
        <div class="error" v-if="$v.obl.$error">
          <template v-if="!$v.obl.alpha">
            Область должна содержать только буквы
          </template>
        </div>
      </div>


      <!-- Город-->
      <div class="field">
        <label>Город(*)</label>
        <input
            type="text"
            name="city"
            v-model="city"
            @blur="$v.city.$touch()">
        <div class="error" v-if="$v.city.$error">
          <template v-if="!$v.city.alpha">
            Город должен содержать только буквы
          </template>
          <template v-else>
            Город обязательный для заполнения
          </template>
        </div>
      </div>


      <!-- Улица-->
      <div class="field">
        <label>Улица</label>
        <input
            type="text"
            name="street"
            v-model="street"
            @blur="$v.street.$touch()">
        <div class="error" v-if="$v.street.$error">
          <template v-if="!$v.street.alpha">
            Улица должна содержать только буквы
          </template>
        </div>
      </div>


      <!-- Дом-->
      <div class="field">
        <label>Дом</label>
        <input
            type="text"
            name="building"
            v-model="building"
            @blur="$v.building.$touch()">
        <div class="error" v-if="$v.building.$error">
          <template v-if="!$v.building.alpha">
            Дом должен содержать только буквы и цифры
          </template>
        </div>
      </div>
      <div class="tooltip" style="display: none;"><b></b><span></span></div>
    </div>
    <br>


    <!-- Паспорт-->
    <div class="field">
      <div for="name" style="text-align: center;"> Паспорт</div>
      <br>
      <label for="name">Тип документа(*)</label>
      <div id="tip">
        <select v-model="tip" @blur="$v.tip.$touch()">
          <option>Паспорт</option>
          <option>Свидетельство о рождении</option>
          <option>Вод. удостоверение</option>
        </select>
        <div class="error" v-if="$v.tip.$error">
          <template>
            Тип документа обязатеьный для заполения
          </template>
        </div>
      </div>
      <br>
      <div class="field">
        <label>Серия</label>
        <input
            type="text"
            name="ser"
            v-model="ser"
            @blur="$v.ser.$touch()">
        <div class="error" v-if="$v.ser.$error">
          <template v-if="!$v.ser.alpha">
            Серия должна содержать только буквы или цифры
          </template>
        </div>
      </div>
      <div class="field">
        <label>Номер</label>
        <input
            type="text"
            name="num"
            v-model="num"
            @blur="$v.num.$touch()">
        <div class="error" v-if="$v.num.$error">
          <template v-if="!$v.num.alpha">
            Номер должен содержать только цифры
          </template>
        </div>
      </div>
      <div class="field">
        <label>Кем выдан</label>
        <input
            type="text"
            name="vid"
            v-model="vid"
            @blur="$v.vid.$touch()">
        <div class="error" v-if="$v.vid.$error">
          <template v-if="!$v.vid.alpha">
            Поле должно содержать только буквы
          </template>
        </div>

      </div>
      <div class="field">
        <label>Дата выдачи(*)</label>
        <input
            type="text"
            name="dat"
            v-model="dat"
            @blur="$v.dat.$touch()">
      </div>
      <div class="error" v-if="$v.dat.$error">
        <template v-if="!$v.dat.alpha">
          Дата выдачи обязательна для заполнения в формате: ДД.ММ.ГГГГ
        </template>

      </div>
      <div class="tooltip" style="display: none;"><b></b><span></span></div>
    </div>


    <!-- Отправить формут-->
    <button type="submit" :disabled="$v.$invalid">
      Отправить форму
    </button>

  </form>
</template>

<script>
import {maxLength, required} from "vuelidate/lib/validators";


export default {
  data() {
    return {
      surname: null,
      name: null,
      patronymic: "",
      birthDate: null,
      phone:null,
      gender: "",
      users:[],
      user:"",
      SMS:"",
      ind:"",
      country: "",
      obl: "",
      city:null,
      street:"",
      building:"",
      tip:null,
      ser: "",
      num:"",
      vid:"",
      dat:null

    };
  },


  validations: {

    //Фамилия
    surname: {
      required,
      alpha: val => /^[а-яА-ЯёЁa-zA-Z]*$/i.test(val),
    },

    //Имя
    name: {
      required,
      alpha: val => /^[а-яА-ЯёЁa-zA-Z]*$/i.test(val),

    },

    //Отчество
    patronymic: {
      alpha: val => /^[а-яА-ЯёЁa-zA-Z]*$/i.test(val),
    },

    //Дата рождения
    birthDate: {
      required,

      alpha: val => /(0[1-9]|[12][0-9]|3[01])[- /.](0[1-9]|1[012])[- /.](19|20)\d\d/i.test(val),

    },

    //Номер телефона
    phone: {
      required,
      maxLength: maxLength(11),
      alpha: val => /^\+?(\d{1,3})?[- .]?\(?(?:\d{2,3})\)?[- .]?\d\d\d[- .]?\d\d\d\d$/g.test(val),

    },

    //Пол
    gender: {
      //не нужна валидация
    },

    //Группа клиентов
    users: {
      required
    },

    //Лечащий врач
    user: {
      alpha: val => /^[а-яА-ЯёЁa-zA-Z]*$/i.test(val),
    },

    //Не отправлять смс
    SMS: {
      //не нужна валидация
    },

    //Индекс
    ind:{
      alpha: val => /^[0-9]*$/.test(val),
      maxLength: maxLength(6),

    },

    //Страна
    country: {
      alpha: val => /^[а-яА-ЯёЁa-zA-Z]*$/i.test(val),

    },

    //Область
    obl: {

      alpha: val => /^[а-яА-ЯёЁa-zA-Z]*$/i.test(val),
    },

    //Город
    city:{
      required,
      alpha: val => /^[а-яА-ЯёЁa-zA-Z]*$/i.test(val),
    },

    //Улица
    street:{
      alpha: val => /^[а-яА-ЯёЁa-zA-Z]*$/i.test(val),

    },

    //Дом
    building:{
      alpha: val => /^[а-яА-ЯёЁa-zA-Z0-9]*$/i.test(val),

    },

    //Тип документа
    tip:{
      required
    },
    //Серия
    ser: {
      alpha: val => /^[а-яА-ЯёЁa-zA-Z0-9]*$/i.test(val),
    },
    //Номер
    num:{
      alpha: val => /^[0-9]*$/.test(val),

    },
    //Кем выдан
    vid:{
      alpha: val => /^[а-яА-ЯёЁa-zA-Z]*$/i.test(val),

    },
    //Дата выдачи
    dat:{
      required,
      alpha: val => /(0[1-9]|[12][0-9]|3[01])[- /.](0[1-9]|1[012])[- /.](19|20)\d\d/i.test(val),
    },


  },

  methods: {

    someAction() {
      alert('Форма отправлена');
    },
  },
};
</script>





<style scoped>
body, input {
  color: #555;
  font-size: 13px;
  font-family: Helvetica, Arial, sans-serif;
}
form {
  width: 300px;
  margin: 40px auto 0;
  padding: 20px 20px 10px;
  border-radius: 5px;
  border: 1px solid #e1e1e8;
  background-color: #f7f7f9;
  box-shadow: rgba(0,0,0,0.075) 2px 3px 7px;
}
input, button {
  outline: none;
}
.field label {
  display: inline-block;
  width: 80px;
  vertical-align: middle;
}
.field {
  margin-bottom: 10px;
  padding: 0;
}
.field input {
  height: 2em;
  min-width: 196px;
  border-radius: 3px;
  border: 1px solid #d3d3d3;
  box-shadow: inset 0 1px 1px rgba(0,0,0,0.1);
  padding: 0 7px;
  color: #666;
}

.field {
  margin-bottom: 24px;
}

.field > label {
  margin-right: 8px;
}

.error {
  color: red;
}
</style>