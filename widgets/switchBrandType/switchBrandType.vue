<template>
    <div class="switch">
        <h1 class="switch_header">CHOOSE YOUR VEHICLE</h1>
        <div class="switch_btnBlock">
            <button class="switch_btn" :class="{ active: activeTab === 'bodyType' }" @click="activeTab = 'bodyType'">
                BODY TYPE
            </button>
            <button class="switch_btn" :class="{ active: activeTab === 'brand' }" @click="activeTab = 'brand'">
                BRAND
            </button>

        </div>
        <div class="switch_block">
            <template v-if="activeTab === 'brand'">
                <template v-if="isLoadingBrands">
                    <p class="isLoading">Loading brands...</p>
                </template>
                <template v-else>
                    <div v-for="brand in brands" :key="brand.id" class="switch_item">
                        <p class="switch_name">{{ brand.name }}</p>
                        <img :src="brand.img" :alt="brand.name" class="switch_img" />
                    </div>
                </template>
            </template>

            <template v-if="activeTab === 'bodyType'">
                <template v-if="isLoadingBodyTypes">
                    <p class="isLoading">Loading body types...</p>
                </template>
                <template v-else>
                    <div v-for="body in bodyTypes" :key="body.id" class="switch_item">
                        <p class="switch_name">{{ body.name }}</p>
                        <img :src="body.img" :alt="body.name" class="switch_img" />
                    </div>
                </template>
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

interface IBrand {
    id: number;
    name: string;
    img: string;
}

interface IBodyType {
    id: number;
    name: string;
    img: string;
}


const localBrands: IBrand[] = [
    { id: 1, name: 'Audi', img: '/local/brand/audi.png' },
    { id: 2, name: 'BMW', img: '/local/brand/bmw.png' },
    { id: 3, name: 'Ford', img: '/local/brand/ford.png' },
    { id: 4, name: 'Lexus', img: '/local/brand/lexus.png' },
    { id: 5, name: 'Mercedes', img: '/local/brand/mercedes.png' },
    { id: 6, name: 'Mitsubishi', img: '/local/brand/mitsubishi.png' },
    { id: 7, name: 'Subaru', img: '/local/brand/subaru.png' },
    //{ id: 8, name: 'Toyota', img: '/local/brand/toyota.png' },

];

const localBodyTypes: IBodyType[] = [
    { id: 1, name: 'SUV', img: '/local/type/suv.png' },
    { id: 2, name: 'Sedan', img: '/local/type/sedan.png' },
    { id: 3, name: 'Coupe', img: '/local/type/coupe.png' },
    { id: 4, name: 'Cab chassis', img: '/local/type/cabChassis.png' },
    { id: 5, name: 'Hatch', img: '/local/type/hatch.png' },
    { id: 6, name: 'Ute', img: '/local/type/ute.png' },
 //   { id: 7, name: 'Wagon', img: '/local/type/wagon.png' },
 //   { id: 8, name: 'Convertible', img: '/local/type/convertible.png' },

];




type TabType = 'brand' | 'bodyType'

const activeTab = ref<TabType>('bodyType')

const brands = ref<IBrand[]>(localBrands);
const bodyTypes = ref<IBodyType[]>(localBodyTypes);

const config = useRuntimeConfig()

const isLoadingBrands = ref(false)
const isLoadingBodyTypes = ref(false)

const fetchBrand = async () => {
    isLoadingBrands.value = true;
    const { data, error } = await useFetch<IBrand[]>(`${config.public.apiBase}/api/brand`);

    if (!error.value && data.value) {
        brands.value = data.value.slice(0, 6).map((brand) => ({
            ...brand,
            img: `${config.public.apiBase}/${brand.img}`,
        }));
    } else {
        console.log('Ошибка при загрузке брендов, используем локальные данные');
    }
    isLoadingBrands.value = false;
};

const fetchBodyType = async () => {
    isLoadingBodyTypes.value = true;
    const { data, error } = await useFetch<IBodyType[]>(`${config.public.apiBase}/api/type`);

    if (!error.value && data.value) {
        bodyTypes.value = data.value.slice(0, 7).map((body) => ({
            ...body,
            img: `${config.public.apiBase}/${body.img}`,
        }));
    } else {
        console.log('Ошибка при загрузке типов кузова, используем локальные данные');
    }
    isLoadingBodyTypes.value = false;
};


onMounted(async () => {
    await fetchBrand();
    await fetchBodyType();
});



</script>

<style scoped lang="scss">
.switch {
    padding: 0 50px 60px;
    justify-content: center;
    align-items: center;
}

.switch_header {
    text-align: center;
    font: 500 normal 24px/100% 'EurostileExtBold';
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
    color: black;
    border: 1px solid white;
    cursor: pointer;
    border-radius: 10px;
    font: 500 normal 16px/100% 'EurostileExtReg';
    backdrop-filter: blur(4px);
    transition: background-color 0.3s, color 0.3s;
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
        transform: scale(1.5);
    }

    p {
        font: 500 normal 14px/100% 'EurostileExtReg';
        color: #4071CB;
    }
}

.switch_showall {
    display: flex;
    justify-content: center;

    &_btn {


        background: transparent;
        color: #4071CB;
        border: 1px solid #4071CB;
        cursor: pointer;
        border-radius: 10px;
        font: 500 normal 14px/100% 'EurostileExtReg';
        padding: 11px 86px;
    }
}
</style>