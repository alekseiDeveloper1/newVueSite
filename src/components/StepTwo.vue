<template>
  <section class="section">
    <div class="_container">
      <div class="section-message">
        Проверьте ваше мероприятие на наличие ошибок, если все в порядке - отправляйте на модерацию.
      </div>
      <div class="section-info">
        <div class="section-info__title">{{Data.title}}</div>
        <div class="section-info__loc">{{Data.town}}{{Data.adress}}</div>
        <div class="section-info__data">{{Data.data1}}, {{Data.data2}}</div>
        <div class="section-info__time">{{Data.time1}}, {{Data.time2}}</div>
        <span>Контакты</span>
        <div class="section-info__phone">{{Data.phone}}</div>
        <div class="section-info__mail">{{Data.email}}</div>
        <div class="section-info__org">{{Data.company}}</div>
        <div class="section-info__subtitle">Организатор мероприятия</div>
      </div>
      <div class="section-img"><picture><source srcset="../assets/tea.webp" type="image/webp"><img src="../assets/tea.jpg" alt="обложка"></picture></div>
      <div class="section-info__descr">{{Data.descr}}</div>
      <button class="section-next__btn btn" v-on:click="back">Назад</button>
      <button class="section-prev__btn btn__color">Отправить на модерацию</button>
    </div>
  </section>
</template>

<script>

export default {
  props: {
    Data: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  methods: {
    back() {
      const main    = document.querySelector('.main'),
            section = document.querySelector('.section');
      section.classList.add('hide');
      main.classList.add('show');
      section.classList.remove('show');
      main.classList.remove('hide');
    },
    
  }
}
</script>

<style>
.section {
  display: none;
  padding: 25px 30px 50px 30px;
}

.section-message {
  position: relative;
  padding: 30px 15px 30px 90px;
  -webkit-box-shadow: 0px 8px 25px 0px #9B63F826;
          box-shadow: 0px 8px 25px 0px #9B63F826;
  margin: 0px 0px 60px 0px;
  font-size: 18px;
  font-weight: 600;
}

.section-message::before {
  content: "";
  position: absolute;
  top: calc(50% - 22.5px);
  left: 25px;
  background: url("../assets/icons/Attention.png") center no-repeat, #FF2998;
  width: 45px;
  height: 45px;
  border-radius: 50%;
}

.section-info {
  position: relative;
  display: inline-block;
  vertical-align: top;
  padding: 0px 40px 0px 66px;
  width: 520px;
  font-size: 18px;
  color: #211536;
}

.section-info span {
  font-weight: 600;
  line-height: 2;
}

.section-info__title {
  font-size: 32px;
  font-weight: 800;
  margin: 0px 30px 32px 0px;
}

.section-info__title::before {
  content: "16+";
  position: absolute;
  top: 0;
  left: 0;
  background: #351767;
  width: 48px;
  height: 48px;
  font-size: 18px;
  font-weight: 600;
  color: #fff;
  text-align: center;
  line-height: 2.7;
}

.section-info__loc {
  position: relative;
  padding: 0px 0px 14px 30px;
}

.section-info__loc::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  background: url("../assets/icons/geo.png") center no-repeat;
  width: 16px;
  height: 21px;
}

.section-info__data {
  position: relative;
  padding: 0px 0px 14px 30px;
}

.section-info__data::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  background: url("../assets/icons/calen.png") center no-repeat;
  width: 16px;
  height: 21px;
}

.section-info__time {
  position: relative;
  padding: 0px 0px 24px 30px;
}

.section-info__time::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  background: url("../assets/icons/clock.png") center no-repeat;
  width: 16px;
  height: 21px;
}

.section-info__phone {
  position: relative;
  padding: 0px 0px 10px 30px;
}

.section-info__phone::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  background: url("../assets/icons/phone.png") center no-repeat;
  width: 16px;
  height: 21px;
}

.section-info__mail {
  position: relative;
  padding: 0px 0px 25px 30px;
}

.section-info__mail::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  background: url("../assets/icons/mail.png") center no-repeat;
  width: 16px;
  height: 21px;
}

.section-info__org {
  color: #211536;
  margin: 0px 0px 2px 0px;
}

.section-info__subtitle {
  color: #8E69CC;
  font-size: 10px;
}

.section-info__descr {
  margin: 20px 0px 20px 0px
}

.section-img {
  display: inline-block;
  width: 630px;
  min-height: 420px;
  margin: 0px 0px 20px 0px;
}

.section-desc {
  color: #211536;
  line-height: 24px;
  margin: 0px 0px 50px 0px;
}

.section-next__btn {
  margin: 0px 20px 0px 0px;
}
</style>