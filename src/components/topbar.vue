<template>
  <div class="fixed z-50 left-0 right-0">
    <nav
      :class="(isTransparent) ? 
        'z-10 py-1 lg:flex lg:justify-between lg:items-center border-gray-300 bg-gray-300  bg-transparent' : 
        'z-10 py-1 lg:flex lg:justify-between lg:items-center border-gray-300 bg-gray-300'"
    >
      <div class="flex items-center justify-between">
        <router-link
          to="/"
          class="
            px-8
            text-xl
            font-bold
            text-gray-100
            lg:text-2xl
            hover:text-indigo-400
            transform hover:scale-110
          "
          >
          <a href="/">
            <img :src = "imgsrc" class="w-64 lg:w-80 hover:cursor-pointer"  alt="LOGO">
          </a>
        </router-link>
        <!-- Mobile menu button -->
        <div @click="toggleNav" class="flex lg:hidden">
          <button
            type="button"
            class="
              text-gray-500
              hover:text-gray-800
              focus:outline-none focus:text-gray-400 
            "
          >
            <svg viewBox="0 0 24 24" class="w-6 h-6 fill-current">
              <path
                fill-rule="evenodd"
                d="M4 5h16a1 1 0 0 1 0 2H4a1 1 0 1 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2z"
              ></path>
            </svg>
          </button>
        </div>
      </div>

      <!-- Mobile Menu open: "block", Menu closed: "hidden" -->
      <ul
        :class="showMenu ? 'flex' : 'hidden'"
        class="
          flex-col
          mt-8
          px-8
          space-y-4
          border-gray-200
          lg:flex lg:space-y-0 lg:flex-row lg:items-center lg:space-x-10 lg:mt-0
        "
      >
        <li class="text-gray-500 font-bold hover:text-gray-800 cursor-pointer"><a href="/#Dep">系所介紹</a></li>
        <li class="text-gray-500 font-bold hover:text-gray-800 cursor-pointer"><a href="/#Lec">課程資訊</a></li>
        <li class="text-gray-500 font-bold hover:text-gray-800 cursor-pointer"><a href="/#Exc">課外生活</a></li>
        <li class="text-gray-500 font-bold hover:text-gray-800 cursor-pointer"><a href="/#Exs">交換學生</a></li>
        <li class="text-gray-500 font-bold hover:text-gray-800 cursor-pointer"><a href="/#Alu">傑出系友</a></li>
        <li class="text-gray-500 font-bold hover:text-gray-800 cursor-pointer"><a href="/#Inf">入學資訊</a></li>
        <li class="text-gray-500 font-bold hover:text-gray-800 cursor-pointer"><a href="/#Qa">常見QA</a></li>
      </ul>
    </nav>
  </div>
</template>

<script>
import { ref } from 'vue';
export default {
  data() {
    let isTransparent = ref(true);
    let showMenu = ref(false);
    return {
        isTransparent,
        showMenu,
        imgsrc : require("../assets/barlogo.webp"),
    }
  },
  setup() {
  },
  mounted() {
    window.addEventListener('scroll', () => {
        let scrollTop = document.documentElement.scrollTop ;
        if ( scrollTop >= 10 ) {
          this.isTransparent = false; 
          this.imgsrc = require("../assets/barlogo.webp");
        }
        else {
          this.isTransparent = true;
          this.imgsrc = require("../assets/barlogo2.webp");
        }
    }, true);
  },
  methods: {
    toggleNav() {
      this.showMenu = !this.showMenu;
      let scrollTop = document.documentElement.scrollTop ;
      if(scrollTop <= 10) {
        this.isTransparent = !this.isTransparent;
      }
    }
  }
};
</script>

<style>
.bg-transparent {
  background-color: transparent !important;
}
nav {
  transition: background-color 0.5s ease, opacity 0.5s ease;
}
</style>