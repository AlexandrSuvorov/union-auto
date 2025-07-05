<template>
    <div class="header">
        <div class="header__top">
            <div class="header__block">
                <form>
                    <select name="language" id="language">
                        <option value="english">English</option>
                        <option value="russia">Russia</option>
                    </select>
                </form>
                <form>
                    <label class="header_currency" for="">Currency:</label>
                    <select name="currency" id="currency">
                        <option value="AED">AED</option>
                        <option value="euro">EURO</option>
                        <option value="dollar">Dollar</option>
                        <option value="ruble">Ruble</option>

                    </select>
                </form>
            </div>
            <div class="header__block">
                <a href="tel:+97146086808" class="header_numberPhone">+ 971 4 608 68 08</a>
                <div>
                    <CallbackButton>Request a callback</CallbackButton>
                </div>
                <div class="header__messengers">
                    <img src="~/assets/image/whatsapp.png" class="header_icon" alt="WhatsApp" />
                    <img src="~/assets/image/telegram.png" class="header_icon" alt="WhatsApp" />
                </div>
            </div>
        </div>
        <hr>
        <div class="header__bottom">
            <img src="/assets/image/logo-hero.png" class="header_logo" alt="">

            <div class="header__links">
                <a href="">FOR SALE</a>
                <a href="">AUTOPARTS</a>
                <a href="">SERVICING</a>
            </div>

            <div class="header__emptystub"></div>
        </div>
    </div>
    <hr>
</template>

<script setup lang="ts">
import CallbackButton from '~/UI/callbackButton.vue';



</script>

<style lang="scss" scoped>
select {
    background-color: transparent;
    border-color: transparent;
    color: white;
    font-family: 'InterFonts', sans-serif;
    font-size: 14px;
    font-weight: 400;
}

hr {
    color: white;
    margin: 0;
    box-shadow: none;
    border: 1px solid;
}

.header {
    &__top {
        display: flex;
        justify-content: space-between;
    }

    &_currency {
        color: white;
        font-family: 'InterDisplayRegular', sans-serif;
        font-size: 14px;
        font-weight: 400;
    }

    &__block {
        display: flex;
        align-items: center;
    }

    &_numberPhone {
        font-family: 'EurostileExtMed', sans-serif;
        font-size: 14px;
        font-weight: 400;
        color: white;
    }

    &__block:nth-child(1) {
        gap: 47px;
        margin: 0 50px;
    }

    &__block:nth-child(2) {
        gap: 30px;
        margin: auto 50px;

    }

    &__messengers {
        display: flex;
        gap: 20px;
    }

    &_icon {
        width: 24px;
        height: 24px;
    }

    &__bottom {
        display: flex;
        justify-content: space-between;
        padding: 0 43px;
    }

    &_logo {
        width: 200px;
        height: 52px;
        margin: 0;
        object-fit: cover;
        object-position: 0 0;
    }

    &__links {
        font-family: 'EurostileExtMed', sans-serif;
        font-size: 14px;
        font-weight: 400;
        color: white;
        display: flex;
        gap: 40px;
        align-items: center;
        justify-content: center;
    }

    &__emptystub {
        width: 200px;
    }
}
</style>
