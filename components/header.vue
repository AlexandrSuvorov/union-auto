<template>
    <div class="container">
        <div class="header">
            <div class="header__top">
                <div class="header__top-dropdowns">
                    <form>
                        <select name="language" id="language">
                            <option value="english">English</option>
                            <option value="russia">Russia</option>
                        </select>
                    </form>
                    <form>
                        <label class="header__top-currency" for="">Currency:</label>
                        <select name="currency" id="currency">
                            <option value="AED">AED</option>
                            <option value="euro">EURO</option>
                            <option value="dollar">Dollar</option>
                            <option value="ruble">Ruble</option>

                        </select>
                    </form>
                </div>
                <div class="header__top-contacts">
                    <a href="tel:+97146086808" class="phone-link">+ 971 4 608 68 08</a>
                    <div>
                        <CallbackButton>Request a callback</CallbackButton>
                    </div>
                    <div class="messenger">
                        <div class="whatsapp">
                            <img src="~/assets/image/whatsapp.png" class="whatsapp-icon" alt="WhatsApp" />
                        </div>
                        <div class="messenger__telegram">
                            <img src="~/assets/image/telegram.png" class="telegram-icon" alt="WhatsApp" />

                        </div>
                    </div>
                </div>
            </div>
            <hr>
            <div class="header__down">
                <div class="header__down-logo">
                    <img src="/assets/image/logo-hero.png" class="logo" alt="">
                </div>
                <div class="header__down-links">
                    <a href="">FOR SALE</a>
                    <a href="">AUTOPARTS</a>
                    <a href="">SERVICING</a>
                </div>
            </div>
        </div>
        <hr>
    </div>
</template>

<script setup lang="ts">
import CallbackButton from '@/UI/CallbackButton.vue';



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

.logo {
    width: 200px;
    height: 52px;
    margin: 0;
    object-fit: cover;
    object-position: 0 0;
}

.phone-link {
    color: white;
    font-family: 'EurostileExtended', sans-serif;
    font-size: 14px;
    font-weight: 400;
}

.header__top {
    display: flex;
    justify-content: space-between;

    &-currency {
        color: white;
        font-family: 'InterFonts', sans-serif;
        font-size: 14px;
        font-weight: 400;
    }

    &-dropdowns,
    &-contacts {
        display: flex;
        align-items: center;
    }

    &-dropdowns {
        gap: 47px;
        margin: 0 50px;
    }

    &-contacts {
        gap: 30px;
        margin: auto 50px;

    }
}


.messenger {
    display: flex;
    gap: 20px;

    .whatsapp-icon {
        width: 24px;
        height: 24px;
    }

    .telegram-icon {
        width: 24px;
        height: 24px;
    }
}

.header__down {
    display: flex;
    padding: 0 43px;

    &-links {
        flex-grow: 1;

        display: flex;
        gap: 40px;
        align-items: center;
        justify-content: center;
    }
}
</style>
