
<template>

<div class="container">
  <div class="row">
    <div class="col-sm-6"></div>

    <form @submit.prevent="someAction()">
    <div class="mb-3">
      <div class="field">
      <label for="formGroupExampleInput" class="form-label">Фамилия</label>
      <input type="text" class="form-control" id="formGroupExampleInput" placeholder="Введите фамилию">
    </div>

  <!-- Фамилия -->

      <label for="name">Фамилия</label>
      <input
          id="surname"
          type="text"
          v-model="surname"
          @blur="$v.surname.$touch()"
      >
      <div class="error" v-if="$v.surname.$error">
        <template v-if="!$v.surname.maxLength">
          Длина Фамилии не должна превышать {{ $v.surname.$params.maxLength.max }} символов
        </template>
        <template v-else-if="!$v.surname.alpha">
          Фамилия должна содержать только буквы
        </template>
        <template v-else>
          Фамилия обязательна для заполнения
        </template>
      </div>
    </div>
    <!-- Имя-->
    <div class="field">
      <label for="name">Имя</label>
      <input
          id="name"
          type="text"
          v-model="name"
          @blur="$v.name.$touch()"
      >
      <div class="error" v-if="$v.name.$error">
        <template v-if="!$v.name.maxLength">
          Длина имени не должна превышать {{ $v.name.$params.maxLength.max }} символов
        </template>
        <template v-else-if="!$v.name.alpha">
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
        <template v-if="!$v.patronymic.maxLength">
          Длина отчества не должна превышать {{ $v.patronymic.$params.maxLength.max }} символов
        </template>
        <template v-else-if="!$v.patronymic.alpha">
          Отчество должно содержать только буквы
        </template>
      </div>
    </div>
    <!-- Дата рождения -->
    <div class="field">
      <label for="birth_date">
        Дата рождения
      </label>
      <input
          id="birth_date"
          type="text"
          v-model="birthDate"
          @blur="$v.birthDate.$touch()"
      >
      <div class="error" v-if="$v.birthDate.$error">
        Дата рождения должна быть в формате ДД.ММ.ГГГГ
      </div>
      <template v-else>
        Фамилия обязательна для заполнения
      </template>

    </div>

    <!-- Номер телефона -->
    <div class="field">
      <label for="name">Номер телефона</label>
      <input
          id="number"
          type="text"
          v-model="number"
          @blur="$v.number.$touch()"
      >
      <div class="error" v-if="$v.number.$error">
        <template v-if="!$v.number.maxLength">
          Длина Номера не должна превышать {{ $v.number.$params.maxLength.max }} символов
        </template>
        <template v-else-if="!$v.number.alpha">
          Номер телефона должен содержать только цифры
        </template>
        <template v-else>
          Номер обязателен для заполнения
        </template>
      </div>
    </div>
    <!-- Пол -->
    <div class="field">
      <label for="name">Пол</label>
      <input
          id="gender"
          type="text"
          v-model="gender"
          @blur="$v.gender.$touch()"
      >
      <div class="error" v-if="$v.gender.$error">
        <template v-if="!$v.gender.maxLength">
          Длина Пола не должна превышать {{ $v.gender.$params.maxLength.max }} символов
        </template>
        <template v-else-if="!$v.gender.alpha">
           Пол должен содержать только буквы
        </template>
      </div>
    </div>
    <!-- Группа клиентов -->
    <div class="field">
      <label for="name">Группа клиентов</label>
      <div><select v-model="users" multiple>
        <option>VIP</option>
        <option>Проблемные</option>
        <option>ОМС</option>
      </select>
      </div>
      <!--<span>Выбрано: {{users}}</span>-->
    </div>
    <!-- Лечащий врач -->
    <div class="field">
      <label for="name">Лечащий врач</label>
    <div id="app">
      <div></div> <select v-model="user">
        <option>Иванов</option>
        <option>Захаров</option>
        <option>Чернышева</option>
      </select>
     <!-- <span>Выбрано: {{user}}</span>-->
    </div>
    </div>
    <div class="field">
      <label for="name">Не отправлять СМС</label>
    <input type="radio" id="yes">
    <label for="yes"> Да</label>
    <br>
    </div>

<!-- Адрес-->
      <div class="field">
        <div><label for="name">Адрес:</label></div>
        <div><label for="name"> Индекс </label>
        <input
            id="ind"
            type="text"
            v-model="ind"
            @blur="$v.ind.$touch()">
        </div>

        <div><label for="name"> Страна </label>
          <input
              id="address"
              type="text"
              v-model="address"
              @blur="$v.address.$touch()">
        </div>


        <div><label for="name"> Область </label>
          <input
              id="obl"
              type="text"
              v-model="obl"
              @blur="$v.obl.$touch()">
        </div>

        <div><label for="name"> Город </label>
          <input
              id="gor"
              type="text"
              v-model="gor"
              @blur="$v.gor.$touch()">
        </div>

        <div><label for="name"> Улица </label>
          <input
              id="ul"
              type="text"
              v-model="ul"
              @blur="$v.ul.$touch()">
        </div>
        <div><label for="name"> Дом </label>
          <input
              id="dom"
              type="text"
              v-model="dom"
              @blur="$v.dom.$touch()">
        </div>






      </div>














    <div class="field">
      <label for="passport_data">
        Серия и номер паспорта
      </label>
      <input id="passport_data" type="text" v-model="passportData">
      <div class="error" v-if="$v.passportData.$invalid">
        Серия и номер паспорта должны быть в формате 1234 567890
      </div>
    </div>





    <button type="submit" :disabled="$v.$invalid">
      Отправить форму
    </button>
  </form>
  </div>
</div>
</template>

<script>
import { required, maxLength } from "vuelidate/lib/validators";
import moment from "moment";

export default {
  data() {
    return {
      passportData: null,
      name: null,
      surname: null,
      patronymic: null,
      birthDate: null,
      number:"+7",
      gender: null,
      users:[],
      user:'',
      address:null

    };
  },

//имя
  validations: {
    name: {
      required,
      maxLength: maxLength(10),
      alpha: val => /^[а-яё]*$/i.test(val),
    },
    //Фамилия
    surname: {
      required,
      maxLength: maxLength(10),
      alpha: val => /^[а-яё]*$/i.test(val),
    },
    //Отчество
    patronymic: {
      required,
      maxLength: maxLength(10),
      alpha: val => /^[а-яё]*$/i.test(val),
    },
    //Дата рождения
    birthDate: {
      required,
      validDate: val => moment(val, "DD.MM.YYYY", true).isValid(),
    },
    //Номер телефона
    number: {
      required,
      maxLength: maxLength(10),
      alpha: val => !/^[\d]{10}$/.test(val),
    },
    //Пол
    gender: {
      required,
      maxLength: maxLength(1),
      alpha: val => /^[а-яё]*$/i.test(val),
    },










    passportData: {
      required,
      validFormat: val => /^\d{4} \d{6}$/.test(val),
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