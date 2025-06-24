<template>
    <div class="container">
        <div class="header">
            <div class="header__dropdowns">
                <form>
                    <select name="language" id="language">
                        <option value="english">English</option>
                        <option value="russia">Russia</option>
                    </select>
                </form>
                <form>
                    <select name="language" id="language">
                        <option value="english">English</option>
                        <option value="russia">Russia</option>
                    </select>
                </form>
            </div>
            <div class="header__contacts">
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
    </div>
</template>

<script setup lang="ts">
import CallbackButton from '@/UI/CallbackButton.vue';


</script>

<style lang="scss">
.header {
    display: flex;
    background-color: red;
    justify-content: space-between;

    &__dropdowns, &__contacts {
        display: flex;
        align-items: center;
    }

    &__dropdowns {
        gap: 47px;
        margin: 19px 50px;
    }
    &__contacts{
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
</style>
