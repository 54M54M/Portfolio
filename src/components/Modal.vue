<template>
  <transition
    enter-active-class="transition-all duration-300 ease-out"
    enter-from-class="opacity-0"
    enter-to-class="opacity-100"
    leave-active-class="transition-all duration-200 ease-in"
    leave-from-class="opacity-100"
    leave-to-class="opacity-0"
  >
    <div
      v-if="isOpen"
      class="fixed inset-0 bg-black/75 backdrop-blur-sm flex justify-center items-center z-50 p-4"
      @click.self="closeModal"
    >
      <transition
        enter-active-class="transition-all duration-300 ease-out"
        enter-from-class="opacity-0 scale-95 translate-y-4"
        enter-to-class="opacity-100 scale-100 translate-y-0"
        appear
      >
        <div
          class="bg-[var(--color-senary)] rounded-xl border-4 border-black shadow-solid w-full max-w-2xl max-h-[90vh] flex flex-col overflow-hidden"
        >
          <!-- Header bar -->
          <div class="p-2 flex items-center border-b-4 gap-2 border-black bg-[var(--color-secondary)]">
            <div class="flex gap-1.5 shrink-0">
              <button
                @click="closeModal"
                class="w-3.5 h-3.5 border-2 border-black rounded-full bg-red-400 hover:bg-red-600 transition-colors duration-150 cursor-pointer"
                title="Cerrar"
              ></button>
              <div class="w-3.5 h-3.5 border-2 border-black rounded-full bg-yellow-400"></div>
              <div class="w-3.5 h-3.5 border-2 border-black rounded-full bg-green-400"></div>
            </div>
            <div class="grow text-center font-black tracking-widest text-xs uppercase text-white">
              — Curriculum Vitae —
            </div>
            <!-- Mirror spacer -->
            <div class="flex gap-1.5 shrink-0 opacity-0 pointer-events-none">
              <div class="w-3.5 h-3.5 rounded-full"></div>
              <div class="w-3.5 h-3.5 rounded-full"></div>
              <div class="w-3.5 h-3.5 rounded-full"></div>
            </div>
          </div>

          <!-- CV Content -->
          <div class="p-6 overflow-y-auto flex-grow font-bold text-gray-800">
            <h1 class="text-2xl font-black mb-1 text-[var(--color-secondary)]">
              Juan Samuel Pérez González
            </h1>
            <p class="text-sm text-gray-500 mb-6">Ingeniero en Sistemas Computacionales</p>

            <!-- Resumen -->
            <h2 class="text-sm font-black tracking-widest uppercase mb-2 pb-1 border-b-2 border-black text-[var(--color-secondary)]">
              Resumen profesional
            </h2>
            <p class="mb-3 text-sm leading-relaxed">
                Ingeniero en Sistemas Computacionales con especialidad en desarrollo de software multiplataforma, enfocado en la
                creación de soluciones digitales atractivas e intuitivas. Tengo experiencia en diseño y desarrollo web, con capacidad para
                desempeñarme tanto en el rol de frontend como en el de backend.
                <br>
                Mis habilidades incluyen:
            </p>
            <ul class="list-disc pl-5 mb-6 text-sm space-y-1">              
                <li>Desarrollo frontend utilizando tecnologías como HTML, CSS (Tailwind, Bootstrap), JavaScript y frameworks.</li>
                <li>Diseño UI responsive centrado en mejorar la interacción y satisfacción del usuario, utilizando herramientas como Figma y Adobe XD.</li>
                <li>Consumo e implementación de API REST y microservicios.</li>
                <li>Desarrollo backend con Python (Flask) y Java (Spring Boot).</li>
                <li>Gestión y modelado de bases de datos relacionales y no relacionales (PostgreSQL, Oracle, MongoDB).</li>
                <li>Aplicación de metodologías ágiles (SCRUM) y herramientas de calidad de código como SonarQube.</li>
                <li>Conocimiento en contenedores (Docker)</li>
            </ul>

            <!-- Experiencia -->
            <h2 class="text-sm font-black tracking-widest uppercase mb-3 pb-1 border-b-2 border-black text-[var(--color-secondary)]">
              Experiencia laboral
            </h2>

            <div
              v-for="(job, i) in experience.items" :key="i"
              class="mb-4 p-3 rounded-lg border-2 border-black bg-white/40"
            >
              <div class="flex justify-between items-start flex-wrap gap-1 mb-1">
                <span class="font-black text-sm">{{ job.position }}</span>
                <span class="text-xs bg-[var(--color-octonary)] text-white px-2 py-0.5 rounded-full border border-black">{{ job.period }}</span>
              </div>
              <p class="text-xs text-gray-600 mb-2 font-semibold">{{ job.company }}</p>
              <p v-for="(desc, di) in job.description" :key="di" class="text-sm leading-relaxed">{{ desc }}</p>
            </div>

            <!-- Aptitudes -->
            <h2 class="text-sm font-black tracking-widest uppercase mb-3 pb-1 border-b-2 border-black text-[var(--color-secondary)]">
              Aptitudes
            </h2>
            <ul class="grid grid-cols-2 md:grid-cols-3 gap-2 mb-4">
              <li v-for="skill in softSkills" :key="skill"
                class="bg-white/60 border-2 border-black rounded-lg px-3 py-1.5 text-sm font-bold text-center shadow-[2px_2px_0_#000]">
                {{ skill }}
              </li>
            </ul>
          </div>

          <!-- Footer CTA -->
          <div class="p-4 border-t-4 border-black text-center bg-[var(--color-octonary)]">
            <p class="mb-3 font-bold text-white text-sm">¿Quieres ver todos los detalles?</p>
            <a
              href="https://drive.google.com/file/d/1Vh_DpVtCMuqUO3_zirK7NTS548dTCvSi/view?usp=sharing"
              target="_blank"
              class="inline-flex items-center gap-2 px-5 py-2 bg-[var(--color-secondary)] text-white rounded-lg font-black text-sm hover:bg-[var(--color-primary)] transition-all shadow-solid border-2 border-black hover:translate-y-[3px] hover:translate-x-[3px] hover:shadow-none"
            >
              <font-awesome-icon icon="fa-solid fa-download" />
              Descargar CV completo
            </a>
          </div>
        </div>
      </transition>
    </div>
  </transition>
</template>

<script>
import { portfolioData } from "../lib/portfolioData";

export default {
  name: 'Modal',
  props: {
    isOpen: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      experience: portfolioData.experience,
      softSkills: [
        'Responsabilidad', 'Trabajo en equipo', 'Comunicación efectiva',
        'Atención al detalle', 'Gestión del tiempo', 'Organización personal'
      ]
    }
  },
  methods: {
    closeModal() {
      this.$emit('close');
    }
  }
}
</script>