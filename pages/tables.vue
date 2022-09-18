<template>
  <div class="h-screen bg-gray-200">

    <div class="p-2 mx-auto max-w-7xl md:flex items-center justify-between">
      <h3 class="text-2xl">
        جدول ها <span class="text-[#616161] text-lg"> پیشرفته</span>
      </h3>
      <div class="flex items-center">
        <nuxt-link to="/" class="text-xs">خانه</nuxt-link>
        <ChevronLeftIcon size="1x" class="px-1"/>
        <nuxt-link to="/tables" class="text-xs"> جدول</nuxt-link>
        <ChevronLeftIcon size="1x" class="px-1"/>
        <nuxt-link to="" class="text-xs">پیشرفته</nuxt-link>
      </div>
    </div>

    <div class="mx-auto max-w-7xl rounded w-full bg-white">

      <h3 class="p-4 text-2xl">
        جدول داده ها مثال 1
      </h3>

      <table class="table-auto w-full">
        <thead>
        <tr class="border-b border-gray-200 ">
          <th class="p-3 border text-gray-700 font-bold text-sm">موتور رندر</th>
          <th class="p-3 border text-gray-700 font-bold text-sm">مرورگر</th>
          <th class="p-3 border text-gray-700 font-bold text-sm"> سیستم عامل</th>
          <th class="p-3 border text-gray-700 font-bold text-sm">ورژن</th>
          <th class="p-3 border text-gray-700 font-bold text-sm">عملیات</th>
        </tr>
        </thead>
        <tbody>
        <tr class="text-center " v-for="(number, k) in numbers" :key="k">

          <td class="border">
            <input class="p-2 w-full" type="text" v-model="number.render_engine"/>
          </td>
          <td class="border">
            <input class="p-2 w-full" type="text" v-model="number.browser"/>
          </td>
          <td class="border">
            <input class="p-2 w-full" type="text" v-model="number.operating_system"
            />
          </td>
          <td class="border">
            <input class="p-2 w-full" type="text" v-model="number.version"
            />
          </td>
          <td class="border">
            <a class="text-white py-1 px-3 rounded-lg bg-red-500 hover:bg-red-600 text-sm"
               @click="deleteRow(k, number)">حذف</a>
          </td>
        </tr>
        </tbody>
      </table>

      <button
        class="m-4 py-2 px-4 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
        @click="addNewRow">
        افزودن سطر
      </button>

    </div>

  </div>
</template>

<script>
import {store} from "~/assets/js";
import {ChevronLeftIcon} from "@vue-hero-icons/outline";

console.log(store);
export default {
  name: 'IndexPage',

  data() {
    return {
      numbers: store.numbers
    }
  },

  components: {
    ChevronLeftIcon,
  },

  methods: {
    deleteRow(index, number) {
      let idx = this.numbers.indexOf(number);
      console.log(idx, index);
      if (idx > -1) {
        store.numbers.splice(idx, 1);
      }
    },
    addNewRow() {
      store.numbers.push({
        render_engine: '',
        browser: '',
        operating_system: '',
        version: '',
        line_total: 0
      })
    }
  }
}
</script>
