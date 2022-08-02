<template>
<header class="header">
    <div class="header__shape">
        <div class="header__shape-inner"></div>
    </div>
    <div class="container">
        <div class="navbar">
            <div class="navbar__row">
                <div class="header__logo"><router-link :to="{ name: 'Home' }" class="header__logo-img"></router-link></div>
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
                                <div class="header__basket-item" v-for="item in 3" :key="item">
                                    <a href="" class="header__basket-link">
                                        <img :src="require('../../src/assets/img/big-pic.jpg')" class="header__basket-img">
                                    </a>
                                    <div class="header__basket-details">
                                        <h5><a class="header__basket-title" href="">محصول شماره یک</a></h5>
                                        <div class="header__basket-price">120000 تومان</div>
                                        <a href="" class="header__basket-remove">حذف</a>
                                    </div>
                                </div>
                                <div class="header__basket-btn">
                                    <a href="cart.html" class="btn btn--boxshadow btn--brand w--100">ثبت و نهایی کردن
                                        سفارش</a>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="header__account">
                        <span class="header__account-icon" @click="showDropDownAccount()"></span>
                        <div class="header__dropdown header__dropdown--w200" :class="{ 'header__dropdown--is-active': isShowAccountDropDown }">
                            <div class="header__dropdown-content">
                                <router-link :to="{ name: 'Home' }" class="header__account-link">ورود</router-link>
                                <router-link :to="{ name: 'Home' }" class="header__account-link">ثبت نام</router-link>
                            </div>
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