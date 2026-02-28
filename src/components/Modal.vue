<template>
    <transition enter-active-class="transition-opacity duration-300" enter-from-class="opacity-0"
        enter-to-class="opacity-100" leave-active-class="transition-opacity duration-300" leave-from-class="opacity-100"
        leave-to-class="opacity-0">
        <div v-if="isOpen" class="fixed inset-0 bg-black bg-opacity-70 flex justify-center items-center z-50"
            @click.self="closeModal">

            <div
                class="bg-[var(--color-senary)] rounded-xl border-4 border-black shadow-solid w-full max-w-4xl max-h-[90vh] flex flex-col overflow-hidden md:mx-80">
                <div class="p-2 flex items-center border-b-2 gap-2 border-black bg-[var(--color-secondary)]">
                    <button class="text-white bg-transparent border-none text-xl cursor-pointer" @click="closeModal">
                        <font-awesome-icon icon="fa-solid fa-times" />
                    </button>
                    <div class="grow text-center font-bold text-white">- Curriculum Vitae -</div>
                    <div class="w-5 h-5 border-2 border-black bg-white rounded-xl" @click="closeModal">
                        <svg class="mx-[-1px] my-[-1px]" width="18" height="18" stroke="#000000" viewBox="0 0 24 24"
                            xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="m18.75 6.82-1.57-1.57L12 10.43 6.82 5.25 5.25 6.82 10.43 12l-5.18 5.18 1.57 1.57L12 13.57l5.18 5.18 1.57-1.57L13.57 12l5.18-5.18Z">
                            </path>
                        </svg>
                    </div>
                </div>

                <div class="p-6 overflow-y-auto flex-grow">
                    <div class="font-sans text-gray-800 font-bold">
                        <h1 class="text-2xl font-bold mb-2 text-[var(--color-secondary)]">Juan Samuel Pérez González
                        </h1>

                        <!-- =========================================================================================== -->

                        <h2
                            class="text-xl font-bold mt-6 mb-3 pb-1 border-b border-gray-200 text-[var(--color-secondary)]">
                            Resumen profesional</h2>
                        <p class="mb-3">Ingeniero en Sistemas Computacionales con especialidad en
                            desarrollo de software multiplataforma, enfocado en la creación de soluciones digitales
                            atractivas e intuitivas. Tengo experiencia en diseño y desarrollo web.</p>
                        <p class="mb-2">Mis habilidades incluyen:</p>
                        <ul class="list-disc pl-5 mb-4">
                            <li>Desarrollo frontend utilizando tecnologías como HTML, CSS (Tailwind), JavaScript y
                                frameworks.</li>
                            <li>Diseño UI centrado en mejorar la interacción y satisfacción del usuario.</li>
                        </ul>

                        <!-- =========================================================================================== -->

                        <h2
                            class="text-xl font-bold mt-6 mb-3 pb-1 border-b border-gray-200 text-[var(--color-secondary)]">
                            Experiencia laboral</h2>

                        <p class="mb-4"><strong>Residencia Profesional • CINVESTAV • Feb - May 2025</strong><br>

                            Durante mi residencia profesional en el CINVESTAV, diseñé y desarrollé una aplicación web
                            orientada a servicios para la gestión de proyectos de investigación. La
                            plataforma permite a usuarios externos consultar proyectos desarrollados en la institución y
                            proporciona un dashboard administrativo para la gestión de la información. El proyecto
                            incluyó el modelado de datos, la implementación de lógica de negocio y el desarrollo de una
                            interfaz intuitiva para mejorar la experiencia del usuario.

                        </p>

                        <!-- =========================================================================================== -->

                        <h2
                            class="text-xl font-bold mt-6 mb-3 pb-1 border-b border-gray-200 text-[var(--color-secondary)]">
                            Aptitudes</h2>
                        <ul class="grid grid-cols-2 md:grid-cols-3 gap-2 mb-4">
                            <li class="bg-gray-100 rounded px-3 py-1">Responsabilidad</li>
                            <li class="bg-gray-100 rounded px-3 py-1">Trabajo en equipo</li>
                            <li class="bg-gray-100 rounded px-3 py-1">Comunicación efectiva</li>
                            <li class="bg-gray-100 rounded px-3 py-1">Atención al detalle</li>
                            <li class="bg-gray-100 rounded px-3 py-1">Gestión del tiempo</li>
                            <li class="bg-gray-100 rounded px-3 py-1">Organización personal</li>
                        </ul>

                        <!-- =========================================================================================== -->

                    </div>
                </div>

                <div class="p-4 border-t-2 border-black text-center bg-[var(--color-octonary)]">
                    <p class="mb-3 font-bold text-white">¿Quieres ver todos los detalles?</p>
                    <a href="https://drive.google.com/file/d/1Vh_DpVtCMuqUO3_zirK7NTS548dTCvSi/view?usp=sharing"
                        target="_blank"
                        class="inline-flex items-center gap-2 px-4 py-2 bg-[var(--color-secondary)] text-white rounded font-bold hover:bg-[var(--color-primary)] transition-all shadow-solid border-2 border-black hover:translate-y-[3px] hover:translate-x-[3px] hover:shadow-none">
                        <font-awesome-icon icon="fa-solid fa-download" /> Descargar CV
                    </a>
                </div>
            </div>

        </div>
    </transition>
</template>

<script>
export default {
    name: 'Modal',
    props: {
        isOpen: {
            type: Boolean,
            default: false
        }
    },
    methods: {
        closeModal() {
            this.$emit('close');
        }
    }
}
</script>
