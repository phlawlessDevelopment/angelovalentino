<script setup>
import NavBar from "./components/NavBar.vue";
import Home from "./components/pages/Home.vue";
import Art from "./components/pages/Art.vue";
import Artist from "./components/pages/Artist.vue";
import Contact from "./components/pages/Contact.vue";
</script>

<template>
  <div class="w-full h-full bg-brandBg text-gray-400">
    <div class="w-full h-full bg-brandBg text-gray-400 slide-in">
      <h1 class="text-5xl text-center w-full p-8">
        {{ wipeLabel }}
      </h1>
    </div>
    <NavBar @change-page="(p) => setPage(p)" />
    <Home />
    <Art />
    <Artist />
    <Contact />
  </div>
</template>

<script>
export default {
  mounted() {
    // slide in reveals
    this.reveals = [...document.querySelectorAll("[class*=anim-wrapper]")];
    this.fadeIns = [...document.querySelectorAll("[class*=fade-in-hidden]")];

    for (let i = 0; i < this.reveals.length; i++) {
      //animate on page load
      setTimeout(() => {
        this.reveals[i].classList.remove("hiding");
      }, (i % 5) * 1000);
    }
    for (let i = 0; i < this.fadeIns.length; i++) {
      this.fadeIns[i].classList.remove("fade-in-hidden");
      this.fadeIns[i].classList.add("fade-in-text");
    }

    //animate on scroll
    document.addEventListener("scroll", (e) => {
      for (let i = 0; i < this.reveals.length; i++) {
        if (!this.isInViewport(this.reveals[i])) {
          this.reveals[i].classList.add("hiding");
        } else {
          setTimeout(() => {
            this.reveals[i].classList.remove("hiding");
          }, (i % 5) * 1000);
        }
      }
      for (let i = 0; i < this.fadeIns.length; i++) {
        if (this.isInViewport(this.fadeIns[i])) {
          this.fadeIns[i].classList.remove("fade-in-hidden");
          this.fadeIns[i].classList.add("fade-in-text");
        } else {
          this.fadeIns[i].classList.remove("fade-in-text");
          this.fadeIns[i].classList.add("fade-in-hidden");
        }
      }
    });
  },
  data() {
    return {
      page: "home",
      wipeLabel: "home",
      revealsHiding: true,
      reveals: [],
      fadeIns: [],
    };
  },
  methods: {
    setPage(page) {
      this.wipeLabel = page;
      let slider = document.querySelector(".slide-in");
      slider.classList.add("slide-in-open");
      setTimeout(() => {
        let yOffset = 0;
        if (page === "Home") {
          yOffset = -100;
        } else if (page === "Artist") {
          yOffset = -150;
        }
        const element = document.getElementById(page);
        const y =
          element.getBoundingClientRect().top + window.pageYOffset + yOffset;
        window.scrollTo({ top: y, behavior: "smooth" });

        slider.classList.remove("slide-in-open");
        slider.classList.remove("slide-in");
        slider.classList.add("slide-out-open");
        slider.classList.add("slide-out");
        setTimeout(() => {
          slider.classList.remove("slide-out-open");
          setTimeout(() => {
            slider.classList.remove("slide-out");
            slider.classList.remove("slide-out-open");
            slider.classList.add("slide-in");
          }, 1200);
        }, 600);
      }, 1200);
    },
    isInViewport(element) {
      const rect = element.getBoundingClientRect();
      return (
        rect.top >= 0 &&
        rect.bottom <=
          (window.innerHeight || document.documentElement.clientHeight)
      );
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  width: 100vw;
  height: 100%;
}
.slide-in {
  padding: 2em 3em;
  position: fixed;
  z-index: 100;
  right: 0;
  bottom: -100%;
  width: 100%;
  transition: all 1.5s ease-in-out;
}
.slide-enter,
.slide-leave-active {
  bottom: -100%;
}
.slide-in-open {
  bottom: 0;
}

.slide-out {
  padding: 2em 3em;
  position: fixed;
  z-index: 100;
  right: 0;
  top: -100%;
  width: 100%;
  transition: all 1.5s ease-in-out;
}
.slide-out-enter,
.slide-out-leave-active {
  top: -100%;
}
.slide-out-open {
  top: 0;
}
.fade-in-hidden {
  opacity: 0;
}
.fade-in-text {
  animation: fadeIn 20s;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
