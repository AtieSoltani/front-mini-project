<template>
  <div class="mx-auto max-w-7xl">

    <div class="flex justify-between border-b border-gray-300">
      <h3 class="py-4 text-lg leading-6 font-medium text-gray-900">
        فرم های عمودی
      </h3>

      <div class="flex items-center">
        <nuxt-link to="/" class="bg-white py-2 px-4 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 hover:bg-gray-50">خانه</nuxt-link>
        <nuxt-link to="/tables" class="mr-4 bg-white py-2 px-4 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 hover:bg-gray-50"> جداول</nuxt-link>
      </div>
    </div>
    <!--sign up form-->
    <div class="py-4 justify-center border-b border-gray-300">

      <!--email-->
      <div class="flex items-center">
        <label class="w-24 pl-4 block font-bold text-gray-700 ">
          ایمیل
        </label>
        <div class="py-2">
          <input
            class="w-96 text-end block border border-gray-200 rounded px-3 py-2 leading-5 text-sm focus:border-indigo-500 focus:ring focus:ring-indigo-500 focus:ring-opacity-50"
            type="email"
            placeholder="ایمیـل"
            v-model="email"
            @blur="$v.email.$touch()"
            :class="{invalid:$v.email.$error}"
          >
          <p class="text-red-400 text-sm font-medium" v-if="!$v.email.email">ایمیل وارد شده معتبر نمیباشد</p>
          <p
            class="text-red-400 text-sm font-medium"
            v-if="!$v.email.required && $v.email.$dirty"
          >لطفا ایمیل را وارد کنید</p>
          <p
            class="text-red-400 text-sm font-medium"
            v-if="!$v.email.maxLength"
          >ایمیل کاربر نمیتواند بیشتر از {{ $v.email.$params.maxLength.max }} کاراکتر داشته باشد</p>
        </div>
      </div>

      <!--password-->
      <div class="flex items-center">
        <label class="w-24 pl-4 block font-bold text-gray-700 ">
          رمز عبور
        </label>
        <div class="py-2">
          <input
            class="w-96 block border border-gray-200 rounded px-3 py-2 leading-5 text-sm focus:border-indigo-500 focus:ring focus:ring-indigo-500 focus:ring-opacity-50"
            type="password"
            placeholder="رمـز عبـور"
            v-model="password"
            @blur="$v.password.$touch()"
            :class="{invalid:$v.password.$error}"
          >
          <p
            class="text-red-400 text-sm font-medium"
            v-if="!$v.password.required && $v.password.$dirty"
          >لطفا کلمه عبور را وارد کنید</p>

          <p
            class="text-red-400 text-sm font-medium"
            v-if="!$v.password.minLength"
          >کلمه عبور باید حداقل شمال {{ $v.password.$params.minLength.min }} کاراکتر باشد</p>
        </div>
      </div>

      <!--phone-->
      <div class="flex items-center">
        <label class="w-24 pl-4 block font-bold text-gray-700 ">
          شماره همراه
        </label>
        <div class="py-2">
          <input
            type="tel"
            pattern="[09]{2}[0-9]{9}"
            class="w-96 block border border-gray-200 rounded px-3 py-2 leading-5 text-sm focus:border-indigo-500 focus:ring focus:ring-indigo-500 focus:ring-opacity-50"
            placeholder="شماره همراه"
            v-model="phone"
            @blur="$v.phone.$touch()"
            :class="{invalid:$v.phone.$error}"
          >
          <p
            class="text-red-400 text-sm font-medium"
            v-if="!$v.phone.required && $v.phone.$dirty"
          >لطفا کلمه شماره همراه خود را وارد کنید</p>

        </div>
      </div>

    </div>

    <div class="py-2 flex justify-start">

      <button type="submit"
              class="inline-flex justify-center py-2 px-5 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
        ورود
      </button>

      <button type="button"
              class="mr-3 bg-white py-2 px-4 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
      انصراف
      </button>

    </div>
    <!--End sign up form-->

  </div>
</template>

<script>
import {validationMixin} from 'vuelidate'
import {
  required,
  maxLength,
  email,
  minLength,
  numeric
} from "vuelidate/lib/validators";

export default {
  mixins: [validationMixin],
  data() {
    return {
      email: "",
      password: "",
      phone: ""
    };
  },
  methods: {},
  validations: {
    email: {
      required,
      email,
      maxLength: maxLength(100),
    },
    password: {
      minLength: minLength(8),
      required
    },
    phone: {
      required,
      numeric,
      maxLength: maxLength(11),
      minLength: minLength(11),
    }
  }
};
</script>

<style>
.invalid {
  border: 1px solid red !important;
  box-shadow: 0 0 5px red !important;
  background-color: lightpink !important;
}

</style>
