<template>
  <div class="font-sans tw-opacity-90">

    <header :class="{ 'bg-color': isScrolled }" class="tw-px-8 lg:tw-fixed tw-top-0 tw-left-0 tw-right-0 tw-z-50">
    <div class="tw-block tw-flex-row tw-flex tw-justify-between tw-items-center tw-px-4 ">
      <div>
        <nuxt-link to="/">
          <h1 class="tw-flex tw-flex tw-flex-col tw-mt-8">
            <span class="tw-text-white tw-font-extrabold lg:tw-text-4xl tw-text-4xl">Seaside</span>
            <span class="tw-text-white tw-font-medium lg:tw-text-2xl tw-text-2xl tw-tranform tw--translate-y-2 tw-translate-x-5">Hotel</span>
          </h1>
        </nuxt-link>
      </div>

      <button @click="toggleMenu" class="tw-flex tw-items-center tw-px-3 tw-py-4 border tw-rounded tw-border-white hover:tw-border-white">
        <svg class="tw-w-10 tw-h-10" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <path d="M4 6H20M4 12H20M4 18H20" stroke="#ffffff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"></path> </g></svg>
      </button>
    </div>

    <nav :class="{ 'tw-hidden': !isOpen }" class="tw-bg-transparent tw-py-2 tw-px-4 lg:tw-flex lg:tw-flex-row lg:tw-justify-evenly lg:tw-mt-1 tw-items-center">
      <ul class="lg:tw-hidden tw-tracking-wide tw-px-2 tw- tw-w-full tw-mt-4 lg:tw-mt-0">
        <li @click="closeMenu">
          <nuxt-link to="/" :class="$route.path === '/' ? 'active' : ''" class="text-black hover:text-blue-800 text-md hover:no-underline">Services</nuxt-link>
        </li>
        <li @click="closeMenu">
          <nuxt-link to="/" :class="$route.path === '/' ? 'active' : ''" class="text-black hover:text-blue-800 text-md hover:no-underline">Works</nuxt-link>
        </li>
        <li @click="closeMenu">
          <nuxt-link to="/" :class="$route.path === '/' ? 'active' : ''" class="text-black hover:text-blue-800 text-md hover:no-underline">About Us</nuxt-link>
        </li>
      </ul>

      <button @click="closeMenu" class="tw-group lg:tw-hidden tw-bg-gray-100 tw-shadow-lg tw-rounded-lg tw-relative tw-h-12 tw-mt-4 tw-cursor-pointer hover:tw-transform hover:tw-translate-x-2 hover:tw-transition-transform hover:tw-duration-300 hover:tw-shadow-2xl-blue-600 hover:tw-shadow-2xl-lg tw-w-48 tw-overflow-hidden tw-rounded-lg tw-text-lg tw-rounded-rt-full">
        <div class="tw-absolute tw-inset-0 tw-w-full tw-bg-gray-100 tw--transition-all tw-duration-[250ms] tw-ease-out"></div>
        <span class="tw-relative tw-inline-flex tw-items-center tw-gap-2 tw-text-black">
          Contacts
        </span>
      </button>
    </nav>
  </header>


    <div class="tw-flex-grow">
      <Nuxt />
    </div>


  </div>
</template>


<script>
  export default {
    data() {
      return {
        isOpen: false,
        theme: 'theme-light',
        selectedItem: null,
        isScrolled: false,
      };
    },


    mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },

  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },

    methods: {

      handleScroll() {
      this.isScrolled = window.scrollY > 0;
    },
      toggleMenu() {
        this.isOpen = !this.isOpen;
      },
      closeMenu() {
        this.isOpen = false;
      },
      closeDialog() {
        this.$emit("close");
      },
      openModal() {
        this.modalVisible = true;
      }

    },



  }

</script>

<style scoped>


  footer {
    background-color: whitesmoke;
  }

  h1 {
    color: #142147;
font-style: normal;
font-weight: 700;
line-height: normal;
  }

  li {
    color: #142147;
font-style: normal;
font-weight: 200;
line-height: normal;
  }


  .bg-color {
    background-color: #FFF500;
  }



  .font-sans {
    font-family: 'Josefin Sans', sans-serif;
    font-family: 'Poppins', sans-serif;
  }

</style>
