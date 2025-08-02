<template>

    <div class="container">
        <div class="main-background">
            <Header />

            <Hero />
        </div>
        <Service/>
        <switchBrandType/>
        <hotDeals/>
    </div>
</template>

<script setup lang="ts">
import Header from '@/components/header.vue';
import Hero from '~/widgets/hero/hero.vue';
import Service from '~/widgets/service/service.vue';
import switchBrandType from '~/widgets/switchBrandType/switchBrandType.vue';
import hotDeals from '~/widgets/hotDeals/hotDeals.vue';
</script>

<style lang="scss">
.main-background {
    background-image: url('/assets/image/hero-background.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;

    border-bottom-right-radius: 30px;
    border-bottom-left-radius: 30px;

}

.header,
.hero {
    background: transparent;
}
</style>