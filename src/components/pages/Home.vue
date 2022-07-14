<template>
  <div class="h-full w-full py-12 px-2 my-12 text-white">
    <div
      v-for="q in quotes"
      :key="q.quote"
      class="text-start home-anim-wrapper hiding p-8"
      id="Home"
    >
      <div class="home-anim">
        <h1 class="text-5xl">"{{ q.quote }}"</h1>
        <h2 class="text-3xl">
          {{ q.from }}
        </h2>
      </div>
    </div>
    <h1 class="absolute bottom-0 pt-8 pb-12 px-96 text-xl fade-in-hidden">
      "This is Art from beyond the fraying edges of society. Stunningly
      beautiful picture-poems of amoral histories, written in light and shadows
      across human forms. This work is of huge human value and impressive to
      behold"
    </h1>
  </div>
</template>

<script>
export default {
  mounted() {},
  data() {
    return {
      quotes: [
        { quote: "PERFECTION", from: "Daniel Lismore" },
        { quote: "CARTMANCY", from: "Edward Lucy-Smith" },
        { quote: "DIGITAL PIONEER", from: "David Burne" },
        { quote: "A SECRETIVE GENIUS", from: "Banksy" },
        { quote: "SHY AND BRILLIANT", from: "Kanye West" },
      ],
    };
  },
  methods: {
  },
};
</script>

<style>
body {
  overflow-x: hidden;
}

.home-anim-wrapper:nth-child(odd) {
  -webkit-transition-duration: 1800ms;
  transition-duration: 1800ms;
}
.home-anim-wrapper:nth-child(even) {
  -webkit-transition-duration: 1200ms;
  transition-duration: 1200ms;
}

.home-anim-wrapper.hiding:nth-child(odd) {
  transform: translate(100%);
  -webkit-transform: translate(100%);
}

.home-anim-wrapper.hiding:nth-child(even) {
  transform: translate(-100%);
  -webkit-transform: translate(-100%);
}

.home-anim {
  content: "";
  display: block;
  margin: auto;
}

</style>
