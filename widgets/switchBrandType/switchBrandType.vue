<template>
    <div class="switch">
        <h1 class="switch_header">CHOOSE YOUR VEHICLE</h1>
        <div class="switch_btnBlock">
            <button class="switch_btn" :class="{ active: activeTab === 'bodyType' }" @click="activeTab = 'bodyType'">
                BODY TYPE
            </button>
            <button class="switch_btn" :class="{ active: activeTab === 'brand' }" @click="activeTab = 'brand'"><!--Реализация переключателя-->
                BRAND
            </button>
            
        </div>
        <div class="switch_block">
            <template v-if="activeTab === 'brand'">
                <div v-for="brand in brands" :key="brand.id" class="switch_item">
                    <p class="switch_name">{{ brand.name }}</p>
                    <img :src="brand.img" :alt="brand.name" class="switch_img">
                </div>
            </template>

            <template v-if="activeTab === 'bodyType'">
                <div v-for="body in bodyTypes" :key="body.id" class="switch_item">
                    <p class="switch_name">{{ body.name }}</p>
                    <img :src="body.img" :alt="body.name" class="switch_img">
                </div>
            </template>
        </div>
        <div class="switch_showall">
            <button class="switch_showall_btn">
                Show all
            </button>
        </div>
    </div>
</template>


<script setup lang="ts">

import { ref, onMounted } from "vue";

interface Brand {
    id: number;
    name: string;
    img: string;
}

interface BodyType {
    id: number;
    name: string;
    img: string;
}

const activeTab = ref<'brand' | 'bodyType'>('bodyType');

const brands = ref<Brand[]>([]);
const bodyTypes = ref<BodyType[]>([]);

const fetchBrand = async () => {
  try {
    const response = await fetch('http://localhost:5000/api/brand');
    const data = await response.json();
    brands.value = data.slice(0, 7).map((brand: Brand) => ({//Выборка 7 значений из бд, а не всех 
      ...brand,
      img: 'http://localhost:5000/' + brand.img,
    }));
  } catch (error) {
    alert('Ошибка при загрузке брендов');
  }
};

const fetchBodyType = async () => {
    try {
        const response = await fetch('http://localhost:5000/api/type');
        const data = await response.json();
        bodyTypes.value = data.slice(0, 7).map((body: BodyType) => ({
        ...body,
            img: 'http://localhost:5000/' + body.img,
        }));
    } catch (error) {
        alert('Ошибка при загрузке типов кузова');
    }
};

onMounted(() => {
    fetchBrand();
    fetchBodyType();
});



</script>

<style scoped lang="scss">
.switch {
    padding: 0 50px;
    justify-content: center;
    align-items: center;
}

.switch_header {
    text-align: center;
    font-family: 'EurostileExtMed', sans-serif;
    font-size: 24px;
    margin-bottom: 20px;
}

.switch_btnBlock {
    display: flex;
    width: 100%;
    margin-bottom: 60px;
}

.switch_btn {
    flex: 1;
    height: 55px;
    background: transparent;
    color: black;
    border: 1px solid white;
    cursor: pointer;
    border-radius: 10px;
    font-family: 'EurostileExtReg', sans-serif;
    font-size: 16px;
    font-weight: 500;
    backdrop-filter: blur(4px);
    transition: background-color 0.3s, color 0.3s;
    padding: 0;

    display: flex;
    justify-content: center;
    align-items: center;

    &:first-child {
        border-right: none;
        border-top-right-radius: 0;
        border-bottom-right-radius: 0;
    }

    &:last-child {
        border-top-left-radius: 0;
        border-bottom-left-radius: 0;
    }

    &.active {
        background-color: #4071CB;
        color: white;
    }
}

.switch_block {
    display: flex;
    gap: 99px;
    margin-top: 16px;
    margin-bottom: 40px;
    &>* {
        flex: 1 1 0;
    }
}

.switch_item {
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    white-space: nowrap;

    img {
        width: 78px;
        height: 72px;
        object-fit: contain;
        margin-bottom: 10px;
    }

    p {
        font-family: 'EurostileExtReg', sans-serif;
        font-size: 14px;
        font-weight: 500;
        color: #4071CB;
    }
}

.switch_showall {
    display: flex;
    justify-content:center ;
    &_btn{

    
    background: transparent;
    color: #4071CB;
    border: 1px solid #4071CB;
    cursor: pointer;
    border-radius: 10px;
    font-family: 'EurostileExtReg', sans-serif;
    font-size: 14px;
    font-weight: 500;
    padding: 11px 86px;
}
}
</style>
