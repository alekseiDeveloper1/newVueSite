<template>
  <main class="main">
    <div class="_container">
      <!-- stepOne -->
      <form @submit.prevent="onSubmit" class="main-form">

        <!-- main-form -->
        <div class="main-form__box box-form">
          <div class="box-form__title">Информация об организаторе</div>
          <div class='form-block _full'>
            <label class="form-block__label">Организатор</label>
            <input v-model="company" name="company" type="text" class="form-block__input">
          </div>
        </div>
        <div class="main-form__box box-form">
          <div class="box-form__title">Контактные данные</div>
          <div class='form-block _small'>
            <label class="form-block__label">Телефон</label>
            <input v-model="phone" name="phone" type="tel" class="form-block__input">
          </div>
          <div class='form-block _small'>
            <label class="form-block__label">E-mail</label>
            <input v-model="email" name="email" type="email" class="form-block__input">
          </div>
          <div class='form-block _small'>
            <label class="form-block__label">Город организатора</label>
            <input v-model="town" name="town" type="text" class="form-block__input">
          </div>
        </div>
        <div class="main-form__box box-form">
          <div class="box-form__title">Общая информация</div>
          <div class='form-block _full'>
            <label class="form-block__label">Название</label>
            <input v-model="title" name="title" type="text" class="form-block__input">
          </div>
        </div>
        <div class="main-form__box box-form">
          <div class='form-block _flex'>
            <label class="form-block__label">Фотография</label>
              <label>
                <div class="form-block__img _ibg"><picture><source srcset="../assets/noImage.webp" type="image/webp"><img src="../assets/noImage.png" alt="обложка"></picture><span class="form-block__span">Главная фотография (обложка мероприятия)</span></div>
                <input type='file' hidden>
              </label>
            <div class="form-block__img _ibg"><picture><source srcset="../assets/tea.webp" type="image/webp"><img src="../assets/tea.jpg" alt="обложка"></picture><span class="form-block__span">Главная фотография (обложка мероприятия)</span><span class="form-block__times times" v-on:click="delDiv">&times;</span></div>
          </div>
        </div>
        <div class="main-form__box box-form">
          <div class='form-block _full'>
            <label class="form-block__label">Подробное описание</label>
            <textarea v-model="descr" name="descr" class="form-block__textarea"></textarea>
          </div>
        </div>

        <!-- main-data -->
        <div class="main-data ">
          <div class="main-data__block" v-bind:class="{data__add: add}">
            <div class="main-data__box box-data">
              <div class="box-data__label">Дата начала</div>
              <div class="data-wrap"><input v-model="data1" name="data1" type="date" class="box-data__input" id="data1"><label for="data1" class="dat"></label></div>
            </div>
            <div class="main-data__box box-data">
              <div class="box-data__label">Время начала</div>
              <div class="data-wrap"><input v-model="time1" name="time1" type="time" class="box-data__input box-data__input_time" id="data2"><label for="data2" class="time"></label></div>
            </div>
            <span></span>
            <div class="main-data__box box-data">
              <div class="box-data__label">Дата окончания</div>
              <div class="data-wrap"><input v-model="data2" name="data2" type="date"  class="box-data__input" id="data3"><label for="data3" class="dat"></label></div>
            </div>
            <div class="main-data__box box-data">
              <div class="box-data__label">Время окончания</div>
              <div class="data-wrap"><input v-model="time2" name="time2" type="time" class="box-data__input box-data__input_time" id="data4"><label for="data4" class="time"></label></div>
            </div>
            <span class="box-data__times times" v-bind:class='{show: add}' v-on:click="delDiv">&times;</span>
          </div>
          
          
        </div>
        <button type="button" class="box-data__btn btn" v-on:click="add = true; addDiv();">+ Добавить дату</button>

        <!-- main-info -->
        <div class="main-info__box box-form">
          <div class='form-block'>
            <label class="form-block__label">Рейтинг мероприятия</label>
            <select v-model="old" name="old" class="form-block__input">
              <option>16+</option>
              <option>14+</option>
              <option>12+</option>
            </select>
          </div>
          <div class='form-block'>
            <label class="form-block__label">Адрес мероприятия</label>
            <input v-model="adress" name="adress" type="text" class="form-block__input">
          </div>
        </div>
        <button type="button" class="main-next__btn btn" v-on:click="reset">Отменить</button>
        <button type='submit' class="main-prev__btn btn__color">Далее</button>
      </form>
      
    </div>
  </main>
  <StepTwo
    v-bind:Data='{company, phone, email, town, title, descr, data1, time1, data2, time2, old, adress}'
  />
  
</template>

<script>
import StepTwo from './StepTwo.vue'

// import { bus } from '../main'
// @ is an alias to /src
export default {
  name: 'Home',
  data() {
    return {
      add: false,
      company: '',
      phone: '',
      email: '',
      town: '',
      title: '',
      descr: '',
      data1: '',
      time1: '',
      data2: '',
      time2: '',
      old: '',
      adress: ''
    }
  },
  components: {
    StepTwo
  },
  methods: {
    addDiv() {
      const body = document.querySelector('.main-data'),
            newDiv = document.createElement('div'),
            oldDiv = document.querySelectorAll('.main-data__block'),
            oldSpan = document.querySelectorAll('.box-data__times');

      oldDiv.forEach(divn => {
        divn.classList.add('data__add');
      });
      oldSpan.forEach(divo => {
        divo.classList.add('show');
      });
      newDiv.classList.add('main-data__block');
      newDiv.innerHTML = `
        <div class="main-data__box box-data">
          <div class="box-data__label">Дата начала</div>
          <div class="data-wrap"><input type="date" class="box-data__input" id="data1"><label for="data1" class="dat"></label></div>
        </div>
        <div class="main-data__box box-data">
          <div class="box-data__label">Время начала</div>
          <div class="data-wrap"><input type="time" value="00:00" class="box-data__input box-data__input_time" id="data2"><label for="data2" class="time"></label></div>
        </div>
        <span></span>
        <div class="main-data__box box-data">
          <div class="box-data__label">Дата окончания</div>
          <div class="data-wrap"><input type="date"  class="box-data__input" id="data3"><label for="data3" class="dat"></label></div>
        </div>
        <div class="main-data__box box-data">
          <div class="box-data__label">Время окончания</div>
          <div class="data-wrap"><input type="time" value="00:00" class="box-data__input box-data__input_time" id="data4"><label for="data4" class="time"></label></div>
        </div>
        <span class="box-data__times times" onclick="delDiv(event)">&times;</span>
      `;
      body.append(newDiv);
      
    },
    delDiv(event) {
      let delEl = event.target.parentNode;
      delEl.parentNode.removeChild(delEl);
    },
    onSubmit() {
      const main    = document.querySelector('.main'),
            section = document.querySelector('.section');
      section.classList.add('show');
      main.classList.add('hide');
      section.classList.remove('hide');
      main.classList.remove('show');
    },
    reset() {
      const form =  document.querySelector('.main-form');
      form.reset();
    }
  }
  
}

</script>
<style>
.main {
  padding: 40px 30px 50px 30px;
}

.main-form__box {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -ms-flex-wrap: wrap;
      flex-wrap: wrap;
  -webkit-box-pack: justify;
      -ms-flex-pack: justify;
          justify-content: space-between;
}

.box-form__title {
  width: 100%;
  font-size: 18px;
  font-weight: 600;
  margin: 0px 0px 40px 0px;
}

._full {
  -webkit-box-flex: 0;
      -ms-flex: 0 1 100%;
          flex: 0 1 100%;
}

._small {
  -webkit-box-flex: 0;
      -ms-flex: 0 1 32%;
          flex: 0 1 32%;
}

._flex {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -ms-flex-wrap: wrap;
      flex-wrap: wrap;
}

.form-block select {
  -webkit-appearance: none;
     -moz-appearance: none;
          appearance: none;
  background: url("../assets/icons/arrow.png") right no-repeat;
  background-position-x: calc(100% - 20px);
}

.form-block__label {
  font-weight: 600;
  line-height: 3;
  width: 100%;
}

.form-block__input {
  font-size: 16px;
  padding: 0px 0px 0px 25px;
  width: 100%;
  height: 58px;
  border: 1px solid #CDB1FB;
  margin: 0px 0px 40px 0px;
}

.form-block__textarea {
  font-size: 16px;
  padding: 20px 0px 0px 25px;
  width: 100%;
  min-height: 193px;
  border: 1px solid #CDB1FB;
  margin: 0px 0px 40px 0px;
}

.form-block__img {
  position: relative;
  width: 126px;
  min-height: 126px;
  margin: 30px 15px 0px 0px;
}

.form-block__img img {
  width: 100%;
  min-height: 126px;
  -o-object-fit: cover;
     object-fit: cover;
}

.form-block__span {
  display: block;
  font-size: 10px;
  line-height: 14px;
  color: #414141;
}

.form-block__times {
  position: absolute;
  right: -14px;
  top: -14px;
  color: #fff;
}

.times {
  width: 30px;
  height: 30px;
  color: #fff;
  border-radius: 50%;
  background: #351767;
  font-size: 28px;
  line-height: 1;
  text-align: center;
  vertical-align: top;
  cursor: pointer;
}

.main-data__block {
  position: relative;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: justify;
      -ms-flex-pack: justify;
          justify-content: space-between;
  margin: 0px 0px 35px 0px;
}

.main-data__block span {
  border-bottom: 2px solid #cdb1fb;
  margin: 0px 15px 29px 0px;
  -webkit-box-flex: 1;
      -ms-flex: 1 1 auto;
          flex: 1 1 auto;
}

.main-data__box {
  -webkit-box-flex: 0;
      -ms-flex: 0 1 22%;
          flex: 0 1 22%;
  margin: 0px 20px 0px 0px;
}

.main-data__box:last-child {
  margin: 0px 0px 0px 0px;
}

.data__add {
  background: #FAF7FE;
  padding: 22px 0px 22px 28px;
}

.data__add span {
  margin: 0px 10px 29px -5px;
}

.box-data__label {
  margin: 0px 0px 10px 0px;
  font-weight: 600;
}

.box-data__input {
  position: relative;
  font-size: 16px;
  min-height: 58px;
  padding: 0px 16px 0px 25px;
  width: 100%;
  border: 1px solid #CDB1FB;
}

.box-data__times {
  position: absolute;
  right: -24px;
  top: -16px;
  display: none;
}

.box-data__btn {
  margin: 0px 0px 50px 0px;
  padding: 19px 22px;
}

.btn {
  border: 1px solid #9B63F8;
  background: #fff;
  font-weight: 600;
  padding: 19px 0px;
  width: 285px;
  text-align: center;
  -webkit-transition: all 0.5s ease 0s;
  -o-transition: all 0.5s ease 0s;
  transition: all 0.5s ease 0s;
  cursor: pointer;
}

.btn:hover {
  background: #9B63F8;
}

.btn__color {
  border: 1px solid #9B63F8;
  background: #9B63F8;
  font-weight: 600;
  width: 285px;
  padding: 19px 0px;
  color: #fff;
  cursor: pointer;
}

.main-next__btn {
  margin: 0px 20px 20px 0px;
}

.dat::after {
  content: "";
  position: absolute;
  top: 0;
  right: 20px;
  width: 18px;
  height: 100%;
  background: url("../assets/icons/calen.png") center no-repeat;
  z-index: 1;
}

.time::after {
  content: "";
  position: absolute;
  top: 0;
  right: 20px;
  width: 18px;
  height: 100%;
  background: url("../assets/icons/clock.png") center no-repeat;
  z-index: 1;
}

input[type=date]::-webkit-calendar-picker-indicator {
  opacity: 0;
  z-index: 2;
}

input[type=time]::-webkit-calendar-picker-indicator {
  opacity: 0;
  z-index: 2;
}

input[type="time" i] {
  -webkit-padding-start: 140px;
          padding-inline-start: 140px;
}

input::-webkit-datetime-edit {
  opacity: 1;
}
.data-wrap {
  position: relative;
}

@media (min-width: 1200px) {
  ._container {
    width: 1200px;
    margin: 0px auto;
  }
}
.show {
  display: block!important;
}
.hide {
  display: none;
}
</style>