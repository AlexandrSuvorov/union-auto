<template>
    <div class="card">
        <div class="card__right">
            <div class="card__right-cars">
                <img src="/assets/image/card-carsforsale.png" class="card__right-img" alt="">
            </div>
        </div>
        <div class="card__left">
            <div class="card__left-autoparts">
                <img src="/assets/image/card-autoparts.png" class="card__left-img" alt="">

            </div>
            <div class="card__left-servicing">
                <img src="/assets/image/card-servicing.png" class="card__left-img" alt="">

            </div>
        </div>

    </div>

</template>


<script setup lang="ts">

</script>

<style lang="scss">
.card {
    display: flex;
    gap: 24px;
    padding: 0 50px;

    &__right {
        &-cars {
            width: 658px;
            height: 640px;
            overflow: hidden;
        }

        &-img {
            object-fit: cover;
            width: 100%;
            height: 100%;
            display: block;
            border-radius: 10px;
        }
    }

    &__left {
        display: flex;
        gap: 24px;
        flex-direction: column;

        &-autoparts,
        &-servicing {
            width: 658px;
            height: 308px;
            overflow: hidden;
            
        }

        &-img {
            object-fit: cover;
            object-position: 50% 75%;
            width: 100%;
            height: 100%;
            display: block;
            border-radius: 10px;
            
        }
    }
}
</style>