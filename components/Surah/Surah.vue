<template>
  <transition name="fade">
    <div
      class="bg-white dark:bg-gray-800 rounded-md p-6 border border-indigo-200 shadow-lg hover:shadow transition duration-200 dark:text-white dark:border-indigo-400"
    >
      <div class="wrap flex justify-between">
        <p>{{ number }}. {{ name }}</p>
      </div>
      <nuxt-link :to="{ name: 'surah-number', params: { number: number } }">
        <p class="text-gray-600 text-sm mt-1 dark:text-gray-500">
          {{ ayat }} Ayat / {{ revelation }}
        </p>
        <div class="flex flex-row-reverse">
          <p class="arabic text-3xl mb-3 text-indigo-700 dark:text-indigo-400">
            {{ arabic_name }}
          </p>
        </div>
        <div class="flex flex-row-reverse">
          <p class="text-gray-600 dark:text-gray-500">{{ translated_name }}</p>
        </div>
      </nuxt-link>
    </div>
  </transition>
</template>

<script>
export default {
  props: [
    "id",
    "number",
    "name",
    "arabic_name",
    "translated_name",
    "ayat",
    "revelation",
    "favorite"
  ]
};
</script>
