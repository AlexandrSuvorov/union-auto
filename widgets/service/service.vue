<script setup lang="ts">
import moreButton from '~/UI/moreButton.vue';
</script>

<template>
    <div class="card">
        <div class="card__right">
            <div class="card__cars">
                <div class="card__block">
                    <h3 class="card__heading">Cars for Sale</h3>
                </div>
                <div class="card__block">
                    <more-button>MORE</more-button>
                </div>
            </div>
        </div>
        <div class="card__left">
            <div class="card__autoparts">
                <div class="card__block">
                    <h3 class="card__heading">Auto Parts</h3>
                </div>
                <div class="card__block">
                    <more-button>MORE</more-button>
                </div>
            </div>
            <div class="card__servicing">
                <div class="card__block">
                    <h3 class="card__heading">Servicing</h3>
                </div>
                <div class="card__block">
                    <more-button>MORE</more-button>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
@mixin card-image($url, $width, $height) {
    width: $width;
    height: $height;
    background-image: url($url);
    background-size: cover;
    background-position: center;
    border-radius: 10px;
}

.card {
    display: flex;
    gap: 24px;
    padding: 0 50px 140px;

    &__block:nth-child(2) {
        align-self: flex-end;
    }

    &__left {
        display: flex;
        flex-direction: column;
        gap: 24px;
        flex: 1 1 0;
    }

    &__right {
        flex: 1 1 0;
        display: flex;
    }

    &__cars,
    &__autoparts,
    &__servicing {
        display: flex;
        justify-content: space-between;
        padding: 30px
    }

    &__cars {
        @include card-image("/assets/image/card-carsforsale.png", 658px, 640px);
    }

    &__autoparts {
        @include card-image("/assets/image/card-autoparts.png", 100%, 308px);
    }

    &__servicing {
        @include card-image("/assets/image/card-servicing.png", 658px, 308px);
    }

    &__heading {
        color: #fff;
        font-size: 24px;
        font-family: 'EurostileExtReg', sans-serif;
        pointer-events: none;
        margin: 0;
    }
}
</style>
