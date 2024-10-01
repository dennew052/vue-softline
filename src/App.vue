<script setup>

import { onMounted, ref } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import 'swiper/swiper-bundle.css'

const items = ref([
  {
    title: 'Решения Softline',
    background: '/vue-softline/bg_section-6-1.png',
    description: 'ГК Softline предлагает клиентам собственную линейку оборудования (ПК, серверы, торговое оборудование и проч.), разработку программных продуктов, облачных решений, решений в области информационной безопасности.'
  },
  {
    title: 'Кибербезопасность',
    background: '/vue-softline/bg_section-6-2.png',
    description: 'Softline обладает всеми необходимыми государственными лицензиями для организации проектов по информационной безопасности и аттестации.'
  },
  {
    title: 'Импортозамещение',
    background: '/vue-softline/bg_section-6-3.png',
    description: 'ГК Softline обладает широчайшим портфелем решений и услуг для импортозамещения, включая ПО и оборудование собственного производства.'
  },
  {
    title: 'Облачные решения',
    background: '/vue-softline/bg_section-6-4.png',
    description: 'Softline использует современные облачные решения как российских, так и международных вендоров для масштабирования бизнеса своих клиентов. Подписки, услуги, трансформация.'
  },
  {
    title: 'Цифровая трансформация и разработка ПО',
    background: '/vue-softline/bg_section-6-5.png',
    description: 'Softline использует современные технологи и новые возможности для увеличения производительности бизнеса заказчика. В штате ГК Softline - 2000+ разработчиков, которые трансформируют ПО под нужды конкретного предприятия.'
  },
  {
    title: 'Техническая поддержка Softline',
    background: '/vue-softline/bg_section-6-6.png',
    description: '200+ инженеров, 24 часа в сутки, 7 дней в неделю, 12 месяцев в году, сервисное партнерство с 30+ мировыми производителями.'
  }
])

const images = ref([
  '/vue-softline/slide-1.png',
  '/vue-softline/slide-2.png',
  '/vue-softline/slide-3.png',
  '/vue-softline/slide-4.png',
  '/vue-softline/slide-5.png'
])

const cities = [
  { name: 'Все', image: '/vue-softline/map-1.png' },
  { name: 'Москва', image: '/vue-softline/map-2.png' },
  { name: 'Центр', image: '/vue-softline/map-3.png' },
  { name: 'Северо-Запад', image: '/vue-softline/map-4.png' },
  { name: 'Юг', image: '/vue-softline/map-5.png' },
  { name: 'Волга', image: '/vue-softline/map-6.png' },
  { name: 'Урал', image: '/vue-softline/map-7.png' },
  { name: 'Сибирь', image: '/vue-softline/map-8.png' },
  { name: 'Дальний Восток', image: '/vue-softline/map-9.png' }
]

const selectCity = (city) => {
  selectedCity.value = city
}

const selectedCity = ref(cities[0])
const activeIndex = ref(-1)
const isWideScreen = ref(window.innerWidth >= 680)

const toggleHeight = (index) => {
  activeIndex.value = activeIndex.value === index ? -1 : index
}

function handleResize() {
  isWideScreen.value = window.innerWidth >= 680
}

const hoverStates = ref(Array(items.value.length).fill(false))

const onMouseOver = (index) => {
  hoverStates.value[index] = true
}

const onMouseLeave = (index) => {
  hoverStates.value[index] = false
}

onMounted(() => {
  window.addEventListener('resize', handleResize)
})


</script>

<template>
  <header class="header">
    <img src="/softlont_logo.png" alt="Logo">
    <nav>
      <a href="#">Облачные решения</a>
      <a href="#">Кибербезопасность</a>
      <a href="#">Импортозамещение</a>
      <a href="#">Цифровая трансформация</a>
    </nav>
  </header>
  <section class="section-1">
    <p>
      Поставщик услуг цифровой трансформации и кибербезопасности
      <a href="#">На сайт</a>
    </p>
  </section>
  <section class="section-2">
    <p><span style="color: #A30C33;">Softline</span> – ведущий поставщик IT-решений и сервисов.* Мы предлагаем
      комплексные IT-решения, облака, программное и аппаратное обеспечение, решения по цифровой трансформации и
      кибербезопасности, а также широкий спектр IT-услуг.</p>
  </section>
  <section class="section-3">
    <p><span>> 30 лет</span><br>на IT-рынке</p>
    <p><span>4600</span><br>сотрудников в России</p>
    <p><span>25</span><br>городов России</p>
    <div></div>
    <p><span>2000 +</span><br>разработчиков</p>
    <p><span>3000 +</span><br>сотрудников ежегодно<br>проходят оценку и обучение</p>
  </section>
  <section class="section-4">
    <div>
      <div>
        <p style="display: inline">Офисы Softline</p>
        <img src="/arrow-down-black.svg" alt="arrow-down" />
      </div>
      <div class="city-list">
      <span
        v-for="city in cities"
        :key="city.name"
        class="city-item"
        @click="selectCity(city)"
        :style="{
          color: selectedCity.name === city.name ? '#A30C33' : '#444444',
          borderBottom: selectedCity.name === city.name ? '2px solid #A30C33' : 'none'
        }"
      >
        {{ city.name }}
      </span>
      </div>
    </div>
    <div class="image-container">
      <img :src="selectedCity.image" alt="City Image" />
    </div>
  </section>
  <section class="section-5">
    <p>Миссия Softline</p>
    <p>Мы помогаем организациям трансформироваться, работать эффективно и безопасно в условиях цифровой экономики.</p>
  </section>
  <section class="section-6">
    <p>Направления бизнеса</p>
    <div
      v-for="(item, index) in items"
      :key="index"
      :style="{
        minHeight: isWideScreen
          ? '260px'
          : (activeIndex === index ? '240px' : '60px'),
        background: hoverStates[index] || !isWideScreen
          ? `linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('${item.background}') no-repeat top`
          : `url('${item.background}') no-repeat top`,
        backgroundSize: 'cover',
        alignContent: hoverStates[index] ? 'start' : 'end',
        justifyContent: hoverStates[index] && activeIndex === index ? 'start' : 'center',
        paddingTop: isWideScreen
          ? '20px'
          : (hoverStates[index] && activeIndex === index ? '20px' : '0'),
      }"
      @click="toggleHeight(index)"
      :class="isWideScreen ? 'clickable-div clickable-div-full' : 'clickable-div'"
      @mouseover="onMouseOver(index)"
      @mouseleave="onMouseLeave(index)"

    >
      <div :style="{
        background: hoverStates[index] || !isWideScreen ? 'none' : 'linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5))',
        height: hoverStates[index] || !isWideScreen ? '40px' : '80px',
        alignItems: hoverStates[index] || !isWideScreen ? 'start' : 'center',
        transition: 'height 0.3s ease',
      }">

        <p>{{ item.title }}</p>
        <img
          :style="{ display: isWideScreen ? 'none' : 'block', alignSelf: 'center' }"
          src="/arrow-down.svg"
          alt="arrow-down">
      </div>
      <p
        :style="{ display: (activeIndex === index && !isWideScreen || isWideScreen && hoverStates[index] ) ? 'block' : 'none' }">
        {{ item.description }}</p>
    </div>
  </section>
  <section class="section-7">
    <p>Компенсационный пакет</p>
    <div>
      <div>
        <img src="/section-7-1.svg" alt="image">
        <p>ДМС</p>
      </div>
      <div>
        <img src="/section-7-2.svg" alt="image">
        <p>Выходной в день рождения</p>
      </div>
      <div>
        <img src="/section-7-3.svg" alt="image">
        <p>Корпоративная мобильная связь</p>
      </div>
      <div>
        <img src="/section-7-4.svg" alt="image">
        <p>Корпоративные скидки на спорт</p>
      </div>
      <div>
        <img src="/section-7-5.svg" alt="image">
        <p>LTI</p>
      </div>
    </div>
    <div style="width: calc(100% - 10px); border: #E4E4E4 solid 1px; margin: 24px 5px"></div>
    <p style="padding-bottom: 5px">Программа дополнительной мотивации</p>
    <p style="color: #B01736">доплата 12% от суммы</p>
    <div>
      <div>
        <img src="/section-7-6.svg" alt="image">
        <p>Оргтехники</p>
      </div>
      <div>
        <img src="/section-7-1.svg" alt="image">
        <p>ДМС</p>
      </div>
      <div>
        <img src="/section-7-7.svg" alt="image">
        <p>Ипотеки</p>
      </div>
    </div>
  </section>
  <section class="section-8">
    <p>Корпоративная жизнь</p>
    <div class="slider-container">
      <swiper
        :pagination="{ clickable: true }"
        :navigation="false"
        :loop="true"
        :space-between="10"
        :autoplay="{ delay: 100, disableOnInteraction: false }"
      >
        <swiper-slide v-for="(image, index) in images" :key="index">
          <img :src="image" alt="Slide Image" />
        </swiper-slide>
      </swiper>
    </div>
  </section>
</template>

<style scoped>
.header {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  padding: 16px 5px;
  gap: 16px;
}

.header img {
  height: 25px;
}

.header nav {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.header a {
  color: #444444;
  font-size: 14px;
  align-content: center;
  vertical-align: center;
  justify-content: center;
  align-self: center;
  align-items: center;
  justify-items: center;
  justify-self: center;
}

.header a:hover {
  color: black;
}

.section-1 {
  background: url('/bg.png') no-repeat bottom;
  width: 100%;
  height: 300px;
}

.section-1 p {
  font-size: 28px;
  max-width: 320px;
  padding-top: 40px;
  padding-left: 5px;
  padding-right: 5px;
}

.section-1 a {
  display: block;
  margin-top: 20px;
  width: 110px;
  height: 32px;
  background-color: #B01736;
  color: white;
  text-align: center;
  align-content: center;
  font-size: 16px;
  border-radius: 8px;
}

.section-2 {
  box-shadow: rgba(100, 100, 111, 0.2) 0 7px 29px 0;
  margin-top: 60px;
  text-align: center;
  display: flex;
  padding: 24px 5px;
}

.section-2 p {
  padding-left: 20px;
  padding-right: 20px;
  align-self: center;
}

.section-3 {
  padding: 50px 28px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  text-align: center;
  gap: 24px;
}

.section-3 div {
  width: 1000px;
  display: none;
}

.section-3 span {
  color: #A30C33;
  font-size: 40px;
}

.section-4 {
  box-shadow: rgba(100, 100, 111, 0.2) 0 7px 29px 0;
  font-size: 20px;
  padding-left: 5px;
  padding-top: 18px;
  padding-bottom: 20px;
}

.section-4 div {
  align-items: baseline;
  justify-content: space-between;
  padding-left: 5px;
}

.section-4 > div > div > img {
  width: 20px;
  height: auto;
  align-self: center;
}

.section-4 div p {
  padding-right: 6px;
}

.section-5 {
  padding: 32px 5px;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: #A30C33;
  background-image: url('/left_pattern.png'), url('/right_pattern.png');
  background-position: left, right;
  background-repeat: no-repeat, no-repeat;
  text-align: center;
}

.section-5 p:nth-child(1) {
  font-size: 28px;
  padding-bottom: 10px;
}

.section-5 p:nth-child(2) {
  font-weight: 400;
}

.section-6 {
  padding-top: 50px;
  justify-content: space-between;
}

.section-6 > p {
  font-size: 28px;
  text-align: center;
  padding-bottom: 15px;
}

.section-6 div p {
  color: white;
  align-self: center;
}

.clickable-div {
  margin-bottom: 10px;
  font-size: 20px;
  transition: min-height 0.3s ease;
  padding-left: 10px;
  padding-right: 17px;
  flex: 0 0 calc(50% - 10px);
  min-height: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.clickable-div div {
  display: flex;
  justify-content: space-between;
}

.clickable-div-full div {
  margin-left: -10px;
  margin-right: -17px;
  padding-left: 10px;
}

.clickable-div > p {
  font-size: 16px;
  font-weight: 400;
  padding-top: 10px;
}

.section-7 {
  text-align: center;
  font-size: 28px;
  box-shadow: rgba(100, 100, 111, 0.2) 0 7px 29px 0;
  margin-top: 50px;
  padding-top: 24px;
}

.section-7 > p {
  padding-bottom: 25px;
}

.section-7 > div {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  column-gap: 40px;
}

.section-7 div div {
  width: 160px;
  height: max-content;
  padding-bottom: 30px;
}

.section-7 div div p {
  font-size: 16px;
  font-weight: 400;
  padding-top: 10px;
}

.section-8 {
  text-align: center;
  font-size: 28px;
  margin-top: 50px;
}

.section-8 p {
  padding-bottom: 15px;
}

.slider-container {
  width: 100%;
  height: auto;
  justify-content: center;
  display: flex;
}

.slider-container img {
  width: 100%;
  height: auto;
  object-fit: cover;
}

.city-list {
  display: flex;
  flex-direction: row;
  overflow-x: auto;
  margin-bottom: 20px;
  margin-top: 20px;
}

.city-item {
  margin-right: 16px;
  cursor: pointer;
  padding-bottom: 20px;
}

.image-container img {
  max-width: 100%;
  height: auto;
}

@media (min-width: 680px) {
  .header {
    padding: 30px 70px;
  }

  .header nav {
    gap: 20px;
  }

  .header a {
    font-size: 18px;
  }

  .section-1 {
    background: url('/bg.png') no-repeat center;
    height: 600px;
  }

  .section-1 p {
    font-size: 56px;
    max-width: 700px;
    padding-top: 158px;
    padding-left: 70px;
  }

  .section-1 a {
    margin-top: 60px;
    font-size: 18px;
    height: 56px;
  }

  .section-2 {
    font-size: 32px;
    margin-left: 70px;
    margin-right: 70px;
    height: 352px;
    padding-top: 100px;
    padding-bottom: 100px;
  }

  .section-3 {
    font-size: 18px;
  }

  .section-3 div {
    display: block;
  }

  .section-3 span {
    font-size: 80px;
  }

  .section-4 div {
    display: flex;
  }

  .section-5 {
    padding: 140px 70px;
  }

  .section-5 p:nth-child(1) {
    font-size: 56px;
    padding-bottom: 40px;
  }

  .section-5 p:nth-child(2) {
    font-size: 32px;
  }

  .section-6 {
    padding-top: 100px;
    display: flex;
    flex-wrap: wrap;
  }

  .section-6 > p {
    font-size: 56px;
    width: 100%;
  }

  .clickable-div {
    font-size: 24px;
    display: block;
    padding-top: 20px;
  }

  .clickable-div > p {
    font-size: 17px;
  }

  .section-7 {
    padding-top: 80px;
  }

  .section-7 > p {
    font-size: 56px;
    padding-bottom: 50px;
  }

  .section-7 > p:nth-child(4) {
    padding-top: 70px;
  }

  .section-7 > p:nth-child(5) {
    padding-bottom: 50px;
  }

}

</style>