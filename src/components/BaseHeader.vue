<template>
<header class="header">
    <div class="header__shape">
        <div class="header__shape-inner"></div>
    </div>
    <div class="container">
        <div class="navbar">
            <div class="navbar__row">
                <div class="header__logo"><router-link href="index.html" class="header__logo-img"></router-link></div>
                <div class="navbar__items">
                    <ul class="navbar__ul">
                        <li class="navbar__item"><a :to="{ name: 'Home' }" class="navbar__link navbar__link--is-active">صفحه اصلی</a></li>
                        <li class="navbar__item navbar__item--has-sub"><router-link :to="{ name: 'Home' }" class="navbar__link">فروشگاه</router-link>
                        </li>
                        <li class="navbar__item"><router-link :to="{ name: 'Home' }" class="navbar__link">درباره ما</router-link></li>
                        <li class="navbar__item"><router-link :to="{ name: 'Home' }" class="navbar__link">تماس باما</router-link></li>
                    </ul>
                </div>
                <div class="navbar__action">
                    <div class="header__basket" @click="showDropDownBasket()">
                        <span class="header__basket-icon"></span>
                        <span class="header__basket-count">0</span>
                        <div class="header__dropdown" :class="{ 'header__dropdown--is-active' : isShowBasketDropDown }">
                            <div class="header__dropdown-content header__dropdown-content--overflow">
                                <p>1</p>
                                <p>1</p>
                                <p>1</p>
                                <p>1</p>
                                <p>1</p>
                                <p>1</p>
                                <p>1</p>
                                <p>1</p>
                                <p>1</p>
                                <p>1</p>
                                <p>1</p>
                            </div>
                        </div>
                    </div>
                    <div class="header__account">
                        <span class="header__account-icon" @click="showDropDownAccount()"></span>
                        <div class="header__dropdown header__dropdown--w200" :class="{ 'header__dropdown--is-active': isShowAccountDropDown }">
                            <div class="header__dropdown-content">account</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</header>
</template>

<script>
export default {
    name: 'BaseHeader',

    data() {
        return {
            isShowBasketDropDown: false,
            isShowAccountDropDown: false,
        }
    },
    methods: {
        showDropDownBasket() {
            this.isShowAccountDropDown = false,
            this.isShowBasketDropDown = !this.isShowBasketDropDown
        },
        showDropDownAccount() {
            this.isShowBasketDropDown = false,
            this.isShowAccountDropDown = !this.isShowAccountDropDown
        },
        eventListener(event) {
        if (! event.target.closest('.header__basket,.header__account')) {
                this.isShowAccountDropDown = false;
                this.isShowBasketDropDown = false;
            }
        }
    },

    mounted() {
    document.addEventListener('click', this.eventListener);
    },

    destroyed() {
        document.removeEventListener('click', this.eventListener);
    }

}
</script>

<style>

</style>