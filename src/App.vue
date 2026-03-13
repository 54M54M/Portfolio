<template>
  <main class="sm:pt-5 relative max-w-screen-md mx-auto p-5">
    <!-- P R E S E N T A C I O N -->
    <TheWindow class="mb-3" :title="portfolioData.presentation.title" color="senary">
      <div class="font-black md:text-center mx-4 text-2xl md:text-5xl">
        Hola, me presento soy <span class="text-[var(--color-secondary)] text-3xl md:text-6xl block">{{
          portfolioData.presentation.name }}</span>
      </div>
      <div class="font-bold mb-2 mx-4 text-sm md:text-lg md:text-center"
        v-for="(paragraph, index) in portfolioData.presentation.description" :key="index">
        {{ paragraph }}
      </div>
    </TheWindow>

    <!-- S O B R E - M I -->
    <div class="flex max-sm:flex-col gap-3 mb-3">
      <TheWindow class="sm:basis-2/3" color="senary" :title="portfolioData.about.title">
        <div class="font-bold text-md mx-4" v-for="(paragraph, index) in portfolioData.about.content" :key="index">
          <div>{{ paragraph }}</div>
          <br v-if="index < portfolioData.about.content.length - 1">
        </div>
      </TheWindow>

      <!-- R E D E S - E - I M A G E N -->
      <div class="flex flex-col">
        <TheWindow class="sm:w-56 bg-[#0C0C0C] hidden md:block" color="quinary" title="¿Yo?">
          <div class="picture">
            <img src="./assets/img/sago.png" alt="Imagen de perfil">
          </div>
        </TheWindow>
        <br class="hidden md:block">

        <!-- R E D E S -->
        <TheWindow class="sm:w-56" color="senary" :title="portfolioData.social.title">
          <br>
          <div class="flex max-sm:flex-col justify-center items-center gap-3">
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <template v-for="(link, index) in portfolioData.social.links" :key="index">
                <a v-if="link.icon !== 'cv'"
                  class="flex items-center justify-center w-12 h-12 text-2xl bg-[var(--color-octonary)] shadow-solid rounded-xl border-4 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100"
                  :href="link.url" target="_blank">
                  <font-awesome-icon :icon="link.icon" style="color: #ececec;" />
                </a>
                <button v-else
                  class="flex items-center justify-center w-12 h-12 text-2xl bg-[var(--color-octonary)] shadow-solid rounded-xl border-4 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100"
                  @click="showCVModal = true">
                  <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" viewBox="0 0 448 512">
                    <path fill="#ececec"
                      d="M224 256A128 128 0 1 0 224 0a128 128 0 1 0 0 256zm-45.7 48C79.8 304 0 383.8 0 482.3C0 498.7 13.3 512 29.7 512H418.3c16.4 0 29.7-13.3 29.7-29.7C448 383.8 368.2 304 269.7 304H178.3z" />
                  </svg>
                </button>
              </template>
            </div>
          </div>
          <br>
        </TheWindow>

        <Modal :isOpen="showCVModal" @close="showCVModal = false" />
      </div>
    </div>

    <!-- H A B I L I D A D E S -->
    <div class="flex max-sm:flex-col gap-3 mb-3 text-center">
      <!-- L E N G U A J E S -->
      <TheWindow color="senary" class="sm:basis-1/3" :title="portfolioData.skills.programming.title">
        <div class="font-bold text-sm mb-2">
          <p>Cuento con experiencia en los siguientes lenguajes:</p>
          <br>
          <div class="flex flex-col items-center gap-3">
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a v-for="(icon, index) in portfolioData.skills.programming.items.slice(0, 3)" :key="index"
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img :src="icon" />
              </a>
            </div>
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a v-for="(icon, index) in portfolioData.skills.programming.items.slice(3)" :key="index + 3"
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img :src="icon" />
              </a>
            </div>
          </div>
        </div>
      </TheWindow>

      <!-- S O F T W A R E -->
      <TheWindow color="senary" class="sm:basis-1/3" :title="portfolioData.skills.software.title">
        <div class="font-bold text-sm mb-2">
          <p>{{ portfolioData.skills.software.description }}</p>
          <br>

          <div class="flex flex-col items-center gap-3">
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a v-for="(icon, index) in portfolioData.skills.software.items.slice(0, 3)" :key="index"
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img :src="icon" />
              </a>
            </div>
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a v-for="(icon, index) in portfolioData.skills.software.items.slice(3)" :key="index + 3"
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img :src="icon" />
              </a>
            </div>
          </div>

        </div>
      </TheWindow>

      <!-- R U T A - A C T U A L -->
      <TheWindow color="senary" class="sm:basis-1/3" :title="portfolioData.skills.learning.title">
        <div class="font-bold text-sm mb-2">
          <p>{{ portfolioData.skills.learning.description }}</p>
          <br>
          
          <div class="flex flex-col items-center gap-3">
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a v-for="(icon, index) in portfolioData.skills.learning.items.slice(0, 3)" :key="index"
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img :src="icon" />
              </a>
            </div>
            <div class="flex flex-wrap justify-center text-2xl gap-2">
              <a v-for="(icon, index) in portfolioData.skills.learning.items.slice(3)" :key="index + 3"
                class="flex items-center justify-center w-10 h-10 text-2xl shadow-solid rounded-xl border-3 border-black hover:translate-y-[5px] hover:translate-x-[5px] hover:shadow-none duration-100">
                <img :src="icon" />
              </a>
            </div>
          </div>

        </div>
      </TheWindow>
    </div>

    <!-- - E X P E R I E N C I A - L A B O R A L - -->
    <!-- TheWindow class="mb-3" :title="portfolioData.experience.title" color="senary">
      <div class="space-y-3 mx-1">
        <div
          v-for="(job, i) in portfolioData.experience.items" :key="i"
          class="experience-card rounded-lg border-2 border-black bg-white/40 p-4 shadow-[3px_3px_0_#000] hover:shadow-[1px_1px_0_#000] hover:translate-x-[2px] hover:translate-y-[2px] transition-all duration-150"
        >
          <div class="flex justify-between items-start flex-wrap gap-2 mb-1">
            <h3 class="font-black text-sm text-[var(--color-secondary)]">{{ job.position }}</h3>
            <span class="text-xs font-bold bg-[var(--color-octonary)] text-white px-2 py-0.5 rounded-full border border-black whitespace-nowrap">
              {{ job.period }}
            </span>
          </div>
          <h4 class="font-bold text-xs text-gray-500 mb-2">{{ job.company }}</h4>
          <ul class="space-y-1">
            <li
              v-for="(desc, di) in job.description" :key="di"
              class="text-sm font-semibold text-gray-700 flex gap-2"
            >
              <span class="text-[var(--color-secondary)] font-black shrink-0">→</span>
              <span>{{ desc }}</span>
            </li>
          </ul>
        </div>
      </div>
    </TheWindow -->

    <!-- P R O Y E C T O S -->
    <TheWindow class="mb-3" :title="portfolioData.projects.title" color="senary">
      <div class="font-bold text-lg mb-2">
        <div class="flex flex-col md:flex-row md:space-x-4">
          <div class="max-w-sm rounded-b-xl">
            <div v-for="(project, index) in projects.slice(0, 3)" :key="index" class="max-w-sm rounded-b-xl pb-3">
              <div class="shadow-2xl rounded-xl bg-[var(--color-senary)]">
                <div v-if="project.images" :id="project.id" class="shadow-2xl rounded-xl bg-[var(--color-senary)]">
                </div>
                <img v-else-if="project.image" class="w-full rounded-t-[10px] rounded-b-[3px]" :src="project.image">
                <div class="px-6 py-4">
                  <div class="font-bold text-xl mb-2">{{ project.title }}</div>
                  <p class="text-gray-700 text-base">{{ project.description }}</p>
                </div>
                <div class="px-6 pb-2">
                  <div class="font-bold text-gray-800 text-sm mb-2">Rol</div>
                  <span v-for="(role, roleIndex) in project.roles" :key="roleIndex"
                    class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">
                    {{ role }}
                  </span>
                </div>
              </div>
            </div>
          </div>

          <div class="max-w-sm rounded-b-xl">
            <div v-for="(project, index) in projects.slice(3)" :key="index + 3" class="max-w-sm rounded-b-xl pb-3">
              <div class="shadow-2xl rounded-xl bg-[var(--color-senary)]">
                <div v-if="project.images" :id="project.id" class="shadow-2xl rounded-xl bg-[var(--color-senary)]">
                </div>
                <img v-else-if="project.image" class="w-full rounded-t-[10px] rounded-b-[3px]" :src="project.image">
                <div class="px-6 py-4">
                  <div class="font-bold text-xl mb-2">{{ project.title }}</div>
                  <p class="text-gray-700 text-base">{{ project.description }}</p>
                </div>
                <div class="px-6 pb-2">
                  <div class="font-bold text-gray-800 text-sm mb-2">Rol</div>
                  <span v-for="(role, roleIndex) in project.roles" :key="roleIndex"
                    class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">
                    {{ role }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </TheWindow>
  </main>
</template>

<script>
import { onMounted, ref, nextTick, computed } from "vue";
import TheWindow from "./components/TheWindow.vue";
import { portfolioData } from "./lib/portfolioData";
import Modal from './components/Modal.vue';

import FundaprogImg from "@/assets/img/fundaprog.png";
import VerdiaImg from "@/assets/img/verdia.png";
import ProdeaImg from "@/assets/img/diseño-figma-PRODEA(Proceso de Documentación Escolar y Académica).png";

import MusicSwipe1 from "@/assets/img/MusicSwipeLog.png";
import MusicSwipe2 from "@/assets/img/MusicSwipeGuest.png";
import MusicSwipe3 from "@/assets/img/MusicSwipeSpotifyUser.png";

import BinGo1 from "@/assets/img/bin-go.png";
import BinGo2 from "@/assets/img/bin-goModalBin.png";

import ControlAcadémico1 from "@/assets/img/ControlAcadémicoLogin1.jpg";
import ControlAcadémico2 from "@/assets/img/ControlAcadémico-HomeStudent.jpg";
import ControlAcadémico3 from "@/assets/img/ControlAcadémico-ProfileStudent.jpg";
import ControlAcadémico4 from "@/assets/img/ControlAcadémico-EditProfile.jpg";
import ControlAcadémico5 from "@/assets/img/ControlAcadémicoLogin2.jpg";
import ControlAcadémico6 from "@/assets/img/ControlAcadémico-HomeAdmin.jpg";
import ControlAcadémico7 from "@/assets/img/ControlAcadémico-DashboardAdmin.jpg";
import ControlAcadémico8 from "@/assets/img/ControlAcadémico-DashboardAdmin-StudentInforation.jpg";

class Carousel {
  constructor(container, images) {
    this.container = container;
    this.images = images;
    this.currentIndex = 0;

    this.render();
    this.addEventListeners();
  }

  render() {
    this.container.innerHTML = `
      <div class="carousel-wrapper relative overflow-hidden">
        <div class="carousel-images flex transition-transform duration-500"
             style="transform: translateX(-${this.currentIndex * 100}%);">
          ${this.images.map((src) => `<img src="${src}" class="w-full rounded-t-[10px] rounded-b-[3px]" alt="Slide">`).join('')}
        </div>
        <button class="carousel-prev absolute top-1/2 left-3 transform -translate-y-1/2 text-white bg-gray-800 bg-opacity-50 p-2 rounded-full">❮</button>
        <button class="carousel-next absolute top-1/2 right-3 transform -translate-y-1/2 text-white bg-gray-800 bg-opacity-50 p-2 rounded-full">❯</button>
      </div>
    `;
  }

  addEventListeners() {
    this.container.querySelector(".carousel-prev").addEventListener("click", () => this.prev());
    this.container.querySelector(".carousel-next").addEventListener("click", () => this.next());
  }

  next() {
    if (this.currentIndex < this.images.length - 1) {
      this.currentIndex++;
      this.update();
    }
  }

  prev() {
    if (this.currentIndex > 0) {
      this.currentIndex--;
      this.update();
    }
  }

  update() {
    const imagesContainer = this.container.querySelector(".carousel-images");
    imagesContainer.style.transform = `translateX(-${this.currentIndex * 100}%)`;
  }
}

export default {
  name: "App",
  components: {
    TheWindow,
    Modal,
  },
  setup() {
    const projectsWithImages = portfolioData.projects.items.map(project => {
      if (project.id === "MusicSwipe") {
        return { ...project, images: [MusicSwipe1, MusicSwipe2, MusicSwipe3] };
      } else if (project.id === "BinGo") {
        return { ...project, images: [BinGo1, BinGo2] };
      } else if (project.id === "ControlAcadémico") {
        return {
          ...project,
          images: [
            ControlAcadémico1, ControlAcadémico2, ControlAcadémico3, ControlAcadémico4,
            ControlAcadémico5, ControlAcadémico6, ControlAcadémico7, ControlAcadémico8
          ]
        };
      } else if (project.id === "Fundaprog") {
        return { ...project, image: FundaprogImg };
      } else if (project.id === "Verdia") {
        return { ...project, image: VerdiaImg };
      } else if (project.id === "Prodea") {
        return { ...project, image: ProdeaImg };
      }
      return project;
    });

    const carouselData = ref(
      projectsWithImages
        .filter(project => project.images)
        .map(({ id, images }) => ({ id, images }))
    );

    onMounted(() => {
      nextTick(() => {
        carouselData.value.forEach(({ id, images }) => {
          const container = document.querySelector(`#${id}`);
          if (container) {
            new Carousel(container, images);
          } else {
            console.warn(`No se encontró el contenedor con ID: ${id}`);
          }
        });
      });
    });

    // Variables para controlar la visualización de experiencias
    const experiencesToShow = ref(2);
    const allExperiences = portfolioData.experience.items;

    // Computed properties
    const visibleExperiences = computed(() => {
      return allExperiences.slice(0, experiencesToShow.value);
    });

    const showLoadMore = computed(() => {
      return allExperiences.length > 4 && experiencesToShow.value < allExperiences.length;
    });

    // Método para cargar más experiencias
    const loadMoreExperiences = () => {
      experiencesToShow.value = allExperiences.length;
    };

    const showCVModal = ref(false);

    return {
      portfolioData,
      projects: projectsWithImages,
      carouselData,
      visibleExperiences,
      showLoadMore,
      showCVModal,
      loadMoreExperiences
    };
  },
};
</script>