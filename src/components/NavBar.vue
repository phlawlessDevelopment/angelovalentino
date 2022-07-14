<template>
  
<nav class="border-2 border-gray-200 px-2 sm:px-4 py-2.5 rounded bg-brandBg fixed top-0 w-full z-50">
  <div class="container flex flex-wrap items-center justify-between mx-auto">
    <button @click="handleClick('Home')" class="flex items-center">
        <span class="self-center text-2xl font-semibold whitespace-nowrap text-white">Angelo Valentino</span>
    </button>
    <button data-collapse-toggle="mobile-menu" type="button" class="inline-flex items-center p-2 ml-3 text-sm  rounded-lg md:hidden  focus:outline-none focus:ring-2  text-gray-400 hover:bg-gray-700 focus:ring-gray-600" aria-controls="mobile-menu" aria-expanded="false">
      <span class="sr-only">Open main menu</span>
      <svg class="w-6 h-6" aria-hidden="true" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z" clip-rule="evenodd"></path></svg>
      <svg class="hidden w-6 h-6" aria-hidden="true" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
    </button>
    <div class="hidden w-full md:block md:w-auto" id="mobile-menu">
      <ul class="flex flex-col mt-4 md:flex-row md:space-x-8 md:mt-0 md:text-lg md:font-medium">
        <li>
          <button  @click="handleClick('Art')" class="block py-2 pl-3 pr-4  border-b  md:border-0 md:p-0 text-gray-400 md:hover:text-white hover:bg-gray-700 hover:text-white md:hover:bg-transparent border-gray-700">Art</button>
        </li>
        <li>
          <button  @click="handleClick('Artist')" class="block py-2 pl-3 pr-4 border-b  md:border-0  md:p-0 text-gray-400 md:hover:text-white hover:bg-gray-700 hover:text-white md:hover:bg-transparent border-gray-700">Artist</button>
        </li>
        <li>
          <button @click="handleClick('Contact')" class="block py-2 pl-3 pr-4   md:border-0  md:p-0 text-gray-400 md:hover:text-white hover:bg-gray-700 hover:text-white md:hover:bg-transparent border-gray-700">Contact</button>
        </li>
      </ul>
    </div>
  </div>
</nav>

</template>

<script>
export default {
emits:['changePage'],
methods:{
    handleClick(value){
        this.$emit('changePage',value)
    }
}
}
</script>

<style>

</style>