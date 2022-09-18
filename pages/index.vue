<template>

  <div class="bg-gray-200">

    <div class="p-2 mx-auto max-w-7xl md:flex items-center justify-between">
      <h3 class="text-2xl">
        پروفایل کاربری
      </h3>
      <div class="flex items-center">
        <nuxt-link to="/" class="text-xs">خانه</nuxt-link>
        <ChevronLeftIcon size="1x" class="px-1"/>
        <nuxt-link to="/tables" class="text-xs">مثال ها</nuxt-link>
        <ChevronLeftIcon size="1x" class="px-1"/>
        <nuxt-link to="/signup" class="text-xs">پروفایل</nuxt-link>
      </div>
    </div>

    <div class="mx-auto max-w-7xl md:flex">

      <!--right menu-->
      <div class="my-2 md:ml-6 md:w-1/4 ">

        <!-- profile-->
        <div class="py-4 rounded bg-white border-t-4 border-[#3C8DBC] text-center">
          <img src="~/static/images/user.jpg"
               class="p-0.5 mx-auto w-24 h-24 inline border-gray-300 border-4 rounded-full">
          <h3 class="py-2 text-xl">مینا مک کین</h3>
          <p class="pb-4 text-[#666] text-sm">مهندس نرم افزار</p>
          <div class="py-4 mx-3 flex items-center justify-between border-y">
            <p class="text-sm font-bold">دنبال شونده</p>
            <p class="text-[#72afd2]">1,322</p>
          </div>
          <div class="py-4 mx-3 flex items-center justify-between border-b">
            <p class="text-sm font-bold">دنبال کننده</p>
            <p class="text-[#72afd2]">543</p>
          </div>
          <div class="py-4 mx-3 flex items-center justify-between border-b">
            <p class="text-sm font-bold">دوستان</p>
            <p class="text-[#72afd2]">13,287</p>
          </div>
          <div class="p-3">
            <button class="w-full py-2 bg-[#3c8dbc] text-white rounded-lg border-[#367fa9] hover:bg-[#367fa9]">دنبال
              کردن
            </button>
          </div>
        </div>
        <!--End profile-->

        <!-- about me-->
        <div class="mt-6 rounded bg-white border-t-4 border-[#3C8DBC]">
          <h3 class="p-2 text-xl border-b">درباره ما</h3>
          <div class="py-4 mx-3 items-center justify-between border-b">
            <p class="text-sm font-bold">تحصیلات</p>
            <p class="text-sm text-[#666]">لیسانس نرم افزار کامپیوتر</p>
          </div>
          <div class="py-4 mx-3 items-center justify-between border-b">
            <p class="text-sm font-bold">موقعیت</p>
            <p class="text-sm text-[#666]">ایران، تهران</p>
          </div>
          <div class="py-4 mx-3 items-center justify-between border-b">
            <p class="text-sm font-bold">توانایی ها</p>
            <div class="text-xs flex">
              <p class="mx-1 py-0.5 px-1 rounded bg-[#3c8dbc] text-white">laravel</p>
              <p class="mx-1 py-0.5 px-1 rounded bg-[#f39c12] text-white">PHP</p>
              <p class="mx-1 py-0.5 px-1 rounded bg-[#00c0ef] text-white">Javascript </p>
              <p class="mx-1 py-0.5 px-1 rounded bg-[#dd4b39] text-white">UI Design </p>
            </div>
          </div>
          <div class="py-4 mx-3 items-center justify-between border-b">
            <p class="text-sm font-bold">یادداشت</p>
            <p class="text-sm text-[#666]">لورم ایپسوم متن ساختگی با تولید سادگی نامفهوم از صنعت چاپ و با استفاده از
              طراحان گرافیک است.</p>
          </div>
        </div>
        <!--End about me-->

      </div>
      <!--End right menu-->

      <!-- Tabs -->
      <div class="mb-4 md:flex-1 rounded-lg">

        <ul class="mt-2 flex border-b bg-white">

          <!--tab1-->
          <li class="-mb-px">
            <a class="py-2 px-4 text-[#444] inline-block hover:text-gray-400"
               :class="{'text-gray-300 border-l border-t-4 border-r border-t-[#3C8DBC]' : tab === 'tab1' }"
               href="#"
               @click.prevent="tab = 'tab1'">فعالیت ها</a>
          </li>
          <!--END tab1-->

          <!--tab-->
          <li class="-mb-px">
            <a class="py-2 px-4 text-[#444] inline-block hover:text-gray-400"
               :class="{ 'text-gray-300 border-l border-t-4 border-r border-t-[#3C8DBC]' : tab === 'tab2' }"
               href="#"
               @click.prevent="tab = 'tab2'">تایم لاین</a>
          </li>
          <!--END tab-->

          <!--tab3-->
          <li class="-mb-px">
            <a class="py-2 px-4 text-[#444] inline-block hover:text-gray-400"
               :class="{ 'text-gray-300 border-l border-t-4 border-r border-t-[#3C8DBC]' : tab === 'tab3' }"
               href="#"
               @click.prevent="tab = 'tab3'">تنظیمات</a>
          </li>
          <!--END tab3-->


        </ul>

        <div class="content bg-white px-4 py-4 border-l border-r border-b pt-4">

          <!--tab1-->
          <div v-if="tab === 'tab1'">

            <div v-for="activity in activities" class="my-2">

              <div v-if="activity.state" class="border-b p-4 text-sm">
                <div class="py-2 flex items-center justify-between ">
                  <div class="flex items-center">
                    <img class="w-10 h-10 border-gray-300 border-4 rounded-full" :src="activity.image" alt="">
                    <div class="pr-2">
                      <a class="text-lg font-bold text-[#3C8DBC] hover:">{{ activity.name }}</a>
                      <p class="pt-0.5 text-[#999]">{{ activity.date }}</p>
                    </div>
                  </div>
                  <XIcon @click="activity.state = false" size="1x" class="text-[#97a0b3] hover:text-gray-500"/>
                </div>
                <div class="text-[#666]">{{ activity.body }}</div>
                <div class="py-2 flex">
                  <div class="pl-2 flex items-center text-[#97a0b3] hover:text-gray-500 text-sm">
                    <ChatIcon @click="activity.state = false" size="1x" class=""/>
                    <p class="px-2"> نظر(5)</p>
                  </div>
                  <div class="pl-2 flex items-center text-[#97a0b3] hover:text-gray-500 text-sm">
                    <ShareIcon @click="activity.state = false" size="1x" class=""/>
                    <p class="px-2">اشتراگ گذاری</p>
                  </div>
                  <div class="flex items-center text-[#97a0b3] hover:text-gray-500 text-sm">
                    <ThumbUpIcon @click="activity.state = false" size="1x" class=""/>
                    <p class="px-2">لایک </p>
                  </div>
                </div>
                <input
                  type="text"
                  class=" w-full block border border-gray-200 px-2 py-2 leading-4 text-sm focus:border-indigo-500 focus:ring focus:ring-indigo-500 focus:ring-opacity-50"
                  placeholder="نظر"
                >
              </div>

            </div>

            <div v-if=state1 class="my-2 p-4 text-sm">
              <div class="py-2 flex items-center justify-between ">
                <div class="flex items-center">
                  <img class="w-10 h-10 border-gray-300 border-4 rounded-full" src="~/static/images/user3.jpg" alt="">
                  <div class="pr-2">
                    <a class="text-lg font-bold text-[#3C8DBC] hover:">آدام جونز</a>
                    <p class="pt-0.5 text-[#999]">ارسال شده ۲ روز پیش</p>
                  </div>
                </div>
                <XIcon @click="state1 = false" size="1x" class="text-[#97a0b3] hover:text-gray-500"/>
              </div>
              <div class="py-2 flex">
                <div class="pl-4 w-1/2">
                  <img src="~/static/images/photo1.png" alt="">
                </div>
                <div class="w-1/4">
                  <img class="px-2 pb-3" src="~/static/images/photo2.png" alt="">
                  <img class="px-2" src="~/static/images/photo3.jpg" alt="">
                </div>
                <div class="w-1/4">
                  <img class="px-2 pb-3" src="~/static/images/photo1.png" alt="">
                  <img class="px-2" src="~/static/images/photo2.png" alt="">
                </div>

              </div>
              <div class="py-2 flex">
                <div class="pl-2 flex items-center text-[#97a0b3] hover:text-gray-500 text-sm">
                  <ChatIcon @click="activity.state = false" size="1x" class=""/>
                  <p class="px-2"> نظر(5)</p>
                </div>
                <div class="pl-2 flex items-center text-[#97a0b3] hover:text-gray-500 text-sm">
                  <ShareIcon @click="activity.state = false" size="1x" class=""/>
                  <p class="px-2">اشتراگ گذاری</p>
                </div>
                <div class="flex items-center text-[#97a0b3] hover:text-gray-500 text-sm">
                  <ThumbUpIcon @click="activity.state = false" size="1x" class=""/>
                  <p class="px-2">لایک </p>
                </div>
              </div>
              <input
                type="text"
                class=" w-full block border border-gray-200 px-2 py-2 leading-4 text-sm focus:border-indigo-500 focus:ring focus:ring-indigo-500 focus:ring-opacity-50"
                placeholder="نظر"
              >
            </div>

          </div>

          <!--tab-->
          <div class="px-8" v-if="tab === 'tab2'">

            <ol class="relative border-r-4 border-gray-200">
              <div class="my-4 p-1 -mr-8 w-32 rounded bg-[#dd4b39] text-white text-sm font-bold">
                ۱۲ اردیبهشت ۱۳۹۴
              </div>

              <li class="mb-10 mr-6">
                <div
                  class="flex absolute -right-4 justify-center items-center w-7 h-7 bg-[#0073b7] rounded-full">
                  <MailIcon size="1.25x" class="text-white"/>
                </div>

                <div class="p-4 bg-gray-100 rounded-lg border border-gray-300 shadow-sm">
                  <div class="pb-2 flex justify-between border-b border-gray-300 items-center">
                    <div class="text-[#555]"><span class="text-[#3c8dbc] font-bold">تیم پشتیبانی</span> یک ایمیل برای
                      شما ارسال کرد
                    </div>
                    <div class="text-sm text-[#999]">12:05</div>
                  </div>
                  <div class="py-2 text-[#444] text-sm">
                    لورم ایپسوم متن ساختگی با تولید سادگی نامفهوم از صنعت چاپ و با استفاده از طراحان گرافیک است. چاپگرها
                    و متون بلکه روزنامه و مجله در ستون و سطرآنچنان که لازم است و برای شرایط فعلی تکنولوژی مورد نیاز و
                    کاربردهای متنوع با هدف بهبود ابزارهای کاربردی می باشد.
                  </div>
                  <div class="flex">
                    <button
                      class="ml-2 text-xs text-white py-1 px-2 border-[#367fa9] bg-[#3c8dbc] rounded hover:bg-[#367fa9]">
                      ادامه
                    </button>
                    <button
                      class="text-xs text-white py-1 px-2 border-[#d73925] bg-[#dd4b39] rounded hover:bg-[#d73925]">
                      حذف
                    </button>
                  </div>
                </div>
              </li>

              <li class="mb-10 mr-6">
                <div
                  class="flex absolute -right-4 justify-center items-center w-7 h-7 bg-[#00c0ef] rounded-full">
                  <UserIcon  size="1.25x" class="text-white"/>
                </div>

                <div class="p-4 bg-gray-100 rounded-lg border border-gray-300 shadow-sm">
                  <div class="pb-2 flex justify-between items-center">
                    <div class="text-[#555]"><span class="text-[#3c8dbc] font-bold">سارا </span>درخواست دوستی شما را قبول کرد
                    </div>
                    <div class="text-sm text-[#999]"> 5 دقیقه پیش</div>
                  </div>
                </div>
              </li>

              <li class="mb-10 mr-6">
                <div
                  class="flex absolute -right-4 justify-center items-center w-7 h-7 bg-[#f39c12] rounded-full">
                  <ChatIcon size="1.25x" class="text-white"/>
                </div>

                <div class="p-4 bg-gray-100 rounded-lg border border-gray-300 shadow-sm">
                  <div class="pb-2 flex justify-between border-b border-gray-300 items-center">
                    <div class="text-[#555]"><span class="text-[#3c8dbc] font-bold">جواد</span>در پست شما نظر گذاشت
                    </div>
                    <div class="text-sm text-[#999]"> 27 دقیقه پیش</div>
                  </div>
                  <div class="py-2 text-[#444] text-sm">
                    لورم ایپسوم متن ساختگی با تولید سادگی نامفهوم از صنعت چاپ و با استفاده از طراحان گرافیک است.
                  </div>
                  <div class="flex">
                    <button
                      class="ml-2 text-xs text-white py-1 px-2 border-[#eea236] bg-[#f39c12] rounded hover:bg-[#eea236]">
                      نمایش نظر
                    </button>
                  </div>
                </div>
              </li>

              <div class="my-4 p-1 -mr-8 w-24 rounded bg-[#00a65a] text-white text-sm font-bold">
                ۱۲ خرداد ۱۳۹۴
              </div>

              <li class="mb-10 mr-6">
                <div
                  class="flex absolute -right-4 justify-center items-center w-7 h-7 bg-[#605ca8] rounded-full">
                  <CameraIcon  size="1.25x" class="text-white"/>
                </div>

                <div class="p-4 bg-gray-100 rounded-lg border border-gray-300 shadow-sm">
                  <div class="pb-2 flex justify-between border-b border-gray-300 items-center">
                    <div class="text-[#555]"><span class="text-[#3c8dbc] font-bold">مینا</span> تصویر آپلود کرد
                    </div>
                    <div class="text-sm text-[#999]">2 روز پیش</div>
                  </div>
                  <div class="py-2 flex">
                    <img class="pl-2 w-32 h-32" src="~/static/images/photo1.png" alt="">
                    <img class="pl-2 w-32 h-32" src="~/static/images/photo2.png" alt="">
                    <img class="pl-2 w-32 h-32" src="~/static/images/photo3.jpg" alt="">

                  </div>
                </div>
              </li>

              <ClockIcon  size="1.25x" class="p-1.5 -mr-4 w-7 h-7 bg-[#d2d6de] rounded-full"/>

            </ol>

          </div>

          <!--tab3-->
          <div v-if="tab === 'tab3'">
            <!--sign up form-->
            <div class="py-4 justify-center">

              <!--name-->
              <div class="md:flex items-center">
                <label class="w-24 pl-4 block font-bold text-gray-700 ">
                  نام
                </label>
                <div class="flex-1 py-2">
                  <input
                    class="w-full block border border-gray-200 rounded px-3 py-2 leading-5 text-sm focus:border-indigo-500 focus:ring focus:ring-indigo-500 focus:ring-opacity-50"
                    type="text"
                    placeholder="نام"
                    required
                  >
                </div>
              </div>

              <!--email-->
              <div class="md:flex items-center">
                <label class="w-24 pl-4 block font-bold text-gray-700 ">
                  ایمیل
                </label>
                <div class="flex-1 py-2">
                  <input
                    class="w-full text-end block border border-gray-200 rounded px-3 py-2 leading-5 text-sm focus:border-indigo-500 focus:ring focus:ring-indigo-500 focus:ring-opacity-50"
                    type="email"
                    placeholder="ایمیـل"
                    required
                  >
                </div>
              </div>

              <!--lastname-->
              <div class="md:flex items-center">
                <label class="w-24 pl-4 block font-bold text-gray-700 ">
                  نام خانوادگی
                </label>
                <div class="py-2 flex-1 ">
                  <input
                    class="w-full block border border-gray-200 rounded px-3 py-2 leading-5 text-sm focus:border-indigo-500 focus:ring focus:ring-indigo-500 focus:ring-opacity-50"
                    type="text"
                    placeholder="نام خانوادگی"
                    required
                  >
                </div>
              </div>

              <!--attributes-->
              <div class="md:flex items-center">
                <label class="w-24 pl-4 block font-bold text-gray-700 ">
                  ویژگی ها
                </label>
                <div class="py-2 flex-1 ">
                  <textarea
                    class="w-full block border border-gray-200 rounded px-3 py-2 text-sm focus:border-indigo-500 focus:ring focus:ring-indigo-500 focus:ring-opacity-50"
                    placeholder="ویژگی ها"
                  />
                </div>
              </div>

              <!--abilities-->
              <div class="md:flex items-center">
                <label class="w-24 pl-4 block font-bold text-gray-700 ">
                  توانایی ها
                </label>
                <div class="py-2 flex-1 ">
                  <input
                    class="w-full block border border-gray-200 rounded px-3 py-2 leading-5 text-sm focus:border-indigo-500 focus:ring focus:ring-indigo-500 focus:ring-opacity-50"
                    type="text"
                    placeholder="توانایی ها"
                    required
                  >
                </div>
              </div>

              <div class="py-4 md:mr-24 flex">
                <input type="checkbox" class="focus:ring-indigo-500 h-4 w-4 text-indigo-600 border-gray-300 rounded">
                <div class="mr-1 flex text-sm">
                  <span class="text-gray-500">من<a class="text-[#3c8dbc] hover:text-blue-400"> قوانین و شرایط</a> را قبول میکنم.</span>
                </div>
              </div>

              <button type="submit" class="md:mr-24 text-white bg-[#dd4b39] hover:bg-[#d73925] font-medium rounded text-sm px-5 py-2 text-center">ارسال</button>

            </div>

            <!--End sign up form-->
          </div>

        </div>
      </div>
      <!--End Tabs -->

    </div>

  </div>

</template>

<script>
import {XIcon, ThumbUpIcon, ShareIcon, ChatIcon, ChevronLeftIcon, MailIcon,UserIcon ,CameraIcon ,ClockIcon } from '@vue-hero-icons/outline'

export default {
  name: "index",
  data() {
    return {
      tab: 'tab1',
      state1: true,
      activities: [
        {
          name: 'جانی آیو',
          image: '_nuxt/static/images/user3.jpg',
          date: 'ارسال شده در ۱۲ اردیبهشت ۱۳۹۶',
          body: 'لورم ایپسوم متن ساختگی با تولید سادگی نامفهوم از صنعت چاپ و با استفاده از طراحان گرافیک است. چاپگرها و متون بلکه روزنامه و مجله در ستون و سطرآنچنان که لازم است و برای شرایط فعلی تکنولوژی مورد نیاز و کاربردهای متنوع با هدف بهبود ابزارهای کاربردی می باشد.',
          state: true,
        },
        {
          name: 'سارا روس',
          image: '_nuxt/static/images/user3.jpg',
          date: 'ارسال شده در ۲ ساعت پیش',
          body: 'لورم ایپسوم متن ساختگی با تولید سادگی نامفهوم از صنعت چاپ و با استفاده از طراحان گرافیک است. چاپگرها و متون بلکه روزنامه و مجله در ستون و سطرآنچنان که لازم است و برای شرایط فعلی تکنولوژی مورد نیاز و کاربردهای متنوع با هدف بهبود ابزارهای کاربردی می باشد.',
          state: true,
        },
      ]
    }
  },
  components: {
    XIcon,
    ThumbUpIcon,
    ShareIcon,
    ChatIcon,
    ChevronLeftIcon,
    MailIcon,
    UserIcon,
    CameraIcon,
    ClockIcon
  }
}
</script>

<style scoped>

</style>

