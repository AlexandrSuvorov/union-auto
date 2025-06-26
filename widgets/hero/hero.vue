<template>
    <div class="hero">
        <div class="hero__heading">
            <div class="hero__title">
                <h1 class="hero__title-text">FIND YOUR NEXT CAR</h1>
            </div>
            <div class="hero__subtitle">
                <h2 class="hero__subtitle-text">PREMIUM CARS FROM DUBAI</h2>
            </div>
        </div>
        <div class="letsgo">
            <div class="element">
                <div class="element__text">
                    LET’S GO
                </div>
            </div>
        </div>
    </div>


</template>

<script setup lang="ts">

</script>

<style lang="scss">
.hero {
    color: white;
    margin-bottom: 90px;
    &__heading {
        margin: 177px 50px;
    }

    &__title {

        &-text {
            font-family: 'EurostileExtMed', sans-serif;
            font-weight: 700;
            font-size: 49px;

        }
    }

    &__subtitle {
        &-text {
            font-family: 'EurostileExtReg', sans-serif;
            font-weight: 400;
            font-size: 39px;

        }
    }

}

.letsgo {
    display: flex;
}

.element {
    margin: auto;
    perspective: 200px;
    display: inline-block;
    width: 362px;
    height: 100px;
}

.element:before {
    border: 2px solid #F1F0EB;
    transform: rotateX(70deg);
    transform-origin: 100% 100%;
    border-radius: 20px 20px 0 0;
    height: 100%;
    width: 100%;
    position: absolute;
    content: '';
    background-color: #F1F0EB;
}

.element__text {
    padding: 80px 0 0;
    text-align: center;
    position: relative;
    z-index: 1;
    color: black;
    font-family: 'EurostileExtMed', sans-serif;
    font-weight: 700;
    font-size: 18px;
}
</style>