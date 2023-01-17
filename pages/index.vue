<template>
  <div class="quran-app">
    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6 mt-6">
      <Surah
        v-for="surah in surah_list"
        :key="surah.number"
        :number="surah.number"
        :name="surah.name.transliteration.id"
        :arabic_name="surah.name.short"
        :translated_name="surah.name.translation.id"
        :ayat="surah.numberOfVerses"
        :revelation="surah.revelation.id"
      ></Surah>
    </div>
    <transition name="slide-fade">
      <success-modal v-if="$store.state.showModal" />
    </transition>
  </div>
</template>

<script>
export default {
  transition: "fade",
  data() {
    return {
      surah_list: [],
      keyword: ""
    };
  },
  async fetch() {
    try {
      const data = await fetch("https://api.quran.gading.dev/surah");
      const res = await data.json();
      this.surah_list = res.data;
      console.log(res.data);

      // console.log(this.surah_list);
    } catch (error) {
      // console.log(error);
    }
  },
  mounted() {
    //get the local favorite surah in mounted lifecycle if SSR is active
    const surah = JSON.parse(window.localStorage.getItem("surah"));
    this.$store.commit("getSurah", surah);
    // this.favorite_surah = JSON.parse(localStorage.getItem("surah"))
  }
};
</script>
