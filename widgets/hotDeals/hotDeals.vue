<script setup lang="ts">
import buttonPrice from '~/UI/buttonPrice.vue';

const config = useRuntimeConfig();

interface ICars {
  id: number;
  brand: string;
  model: string;
  img: string;
  date: number;
  drive: number;
  transmission: string;
  type: string;
  price: number;
}

const localCars: ICars[] = [
  { id: 1, brand: 'BMW', model: 'G30', img: '/local/auto/bmwg30.png', date: 2023, drive: 10.5, transmission: "AWD", type: "Sedan", price: 3942000 },
  { id: 2, brand: 'Lexus', model: 'LX LX500d', img: '/local/auto/lexuslxlx500d.png', date: 2022, drive: 5.7, transmission: "AWD", type: "SUV", price: 3219000 },
  { id: 3, brand: 'Mitsubishi', model: 'Pajero Sport GLX', img: '/local/auto/mitsubishipajerosportglx.png', date: 2022, drive: 2.4, transmission: "AWD", type: "SUV", price: 3491000 },
  { id: 4, brand: 'Lexus', model: 'UX UX200 Luxury', img: '/local/auto/lexusuxux200luxury.png', date: 2022, drive: 2, transmission: "AWD", type: "SUV", price: 2932000 },
  { id: 5, brand: 'Mercedes', model: 'Benz G-Class', img: '/local/auto/mercedesbenzgclass.png', date: 2022, drive: 4, transmission: "AWD", type: "SUV", price: 5932000 },
  { id: 6, brand: 'Honda', model: 'Civic', img: '/local/auto/hondacivic.png', date: 2024, drive: 4, transmission: "AWD", type: "Sedan", price: 2213200 },
  { id: 7, brand: 'Mercedes', model: 'AMG GT', img: '/local/auto/mercedesamggt.png', date: 2022, drive: 6, transmission: "AWD", type: "Sedan", price: 3042000 },
  { id: 8, brand: 'Dodge', model: 'Viper', img: '/local/auto/dodgeviper.png', date: 2022, drive: 8, transmission: "AWD", type: "Sedan", price: 4921000 },

];

const cars = ref<ICars[]>(localCars);
const isLoadingCars = ref(false);

const fetchCars = async () => {
  isLoadingCars.value = true;
  const { data, error } = await useFetch<ICars[]>(`${config.public.apiBase}/api/auto`);

  if (!error.value && data.value) {
    cars.value = data.value.slice(0, 7).map((car) => ({
      ...car,
      img: `${config.public.apiBase}/${car.img}`,
    }));
  } else {
    console.log('Ошибка при загрузке машин, используем локальные данные');
  }
  isLoadingCars.value = false;
};

onMounted(async () => {
  await fetchCars();
});
</script>

<template>
  <section class="hot-deals">
    <h1 class="hot-deals__header">HOT DEALS</h1>
    <template v-if="isLoadingCars">
      <p class="hot-deals__loading">Loading cars...</p>
    </template>
    <template v-else>
      <div class="hot-deals__list">
        <article v-for="car in cars" :key="car.id" class="hot-deals__card">
          <header class="card__header">
            <h2 class="card__title">{{ `${car.brand} ${car.model}` }}</h2>
            <span class="card__tag card__tag--new">&bull;NEW</span>
          </header>
          <p class="card__date">{{ car.date }}</p>
          <div class="card__image-wrapper">
            <img :src="car.img" :alt="car.model" class="card__image" />
            <div class="card__brand">{{ car.brand }}</div>
          </div>
          <div class="card__features features">
            <div class="features__item">
              <img src="/assets/image/drive.svg" class="features__icon" alt="Drive" />
              <p class="features__text">{{ car.drive.toFixed(1) }} L</p>
            </div>
            <div class="features__item">
              <img src="/assets/image/transmission.svg" class="features__icon" alt="Transmission" />
              <p class="features__text">{{ car.transmission }}</p>
            </div>
            <div class="features__item">
              <img src="/assets/image/type.svg" class="features__icon" alt="Type" />
              <p class="features__text">{{ car.type }}</p>
            </div>
          </div>
          <div class="card__button">
            <buttonPrice>{{ car.price }} AED</buttonPrice>
          </div>
        </article>
      </div>
    </template>
  </section>
  <section class="bigImage">
    <div class="bigImage_block">
      <img src="/assets/image/carBigImage.png" alt="" class="bigImage_image">
    </div>
  </section>
</template>

<style lang="scss" scoped>
.hot-deals {
  padding: 0 50px 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  &__header {
    text-align: center;
    font: 500 normal 24px/100% 'EurostileExtReg';
    margin-bottom: 20px;
  }

  &__loading {
    font-size: 16px;
    text-align: center;
  }

  &__list {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(2, 1fr);
    grid-column-gap: 13px;
    grid-row-gap: 34px;
  }

  &__card {
    position: relative;
    display: flex;
    flex-direction: column;
    border: 2px solid lightgray;
    border-radius: 8px;
    overflow: hidden;
    width: 325px;
    height: 325px;
    background-color: #f1f0eb;

    &:hover {
      border-color: #ccc;
      background-color: white;

      .card__brand {
        color: #f1f0eb;

      }
    }
  }
}

.card__header {
  margin: 20px 20px 6px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  & .card__title {
    font: 400 normal 16px/100% 'EurostileExtMed';
    margin: 0;
    position: relative;
    z-index: 2;
  }

  & .card__tag {
    font: 400 normal 10px/100% 'EurostileExtReg';
    position: relative;
    z-index: 2;
    margin: 0;
    color: #4071cb;
  }
}

.card__date {
  margin: 0 20px;
  font: 400 normal 10px/100% 'EurostileExtReg';
  position: relative;
  z-index: 2;
}

.card__image-wrapper {
  position: relative;
  width: 100%;
  height: 140px;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: visible;
  margin: 15px 0;

  .card__image {
    max-width: 100%;
    max-height: 111px;
    object-fit: contain;
    position: relative;
    z-index: 2;
    transform: scale(1.2);
  }

  .card__brand {
    box-sizing: border-box;
    position: absolute;
    top: 15%;
    left: 50%;
    transform: translate(-50%, -50%);
    font: 700 normal 2rem/100% 'EurostileExtMed';
    letter-spacing: 0.5rem;
    color: white;
    pointer-events: none;
    user-select: none;
    z-index: 1;
    transition: color 0.3s ease;
  }
}

.card__features {
  display: flex;
  gap: 20px;
  position: relative;
  z-index: 2;
  margin: 0 20px;

  & .features__item {
    display: flex;
    align-items: center;
  }

  & .features__icon {
    width: 25px;
    height: 22px;
  }

  & .features__text {
    font: 400 normal 8px/100% 'EurostileExtReg';
    margin-left: 5px;
  }
}

.card__button {
  margin: 10px 20px 20px;
}
.bigImage{
  padding: 0px 50px 165px;
  box-sizing: border-box;
}
.bigImage_image{
  width: 100%;
  border-radius: 30px;
}
</style>
