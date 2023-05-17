<template>
    <div class="flex flex-col h-auto w-full font-sans lg:flex-row lg:h-screen">
        <div
            class="flex w-full h-screen bg-dark-900 relative items-center justify-center lg:w-1/2"
        >
            <div
                class="flex w-full items-center px-4 top-4 left-0 gap-4 absolute justify-between lg:px-8"
            >
                <img
                    src="~/assets/logo.svg"
                    alt="logo"
                    loading="lazy"
                    width="32"
                    height="32"
                    class="w-8 h-8"
                />
            </div>
            <template v-for="_d in data" :key="_d.index">
                <PhotoInfo v-if="selected === _d.index" v-motion-slide-bottom>
                    <template #title> {{ _d.title }} </template>
                    <template #subtitle> {{ _d.subtitle }} </template>
                    <template #description> {{ _d.description }} </template>
                </PhotoInfo>
            </template>
        </div>
        <div class="h-screen w-full relative lg:w-1/2">
            <img
                :src="`~/assets/photos_${selected}.jpg`"
                loading="lazy"
                :alt="`project-image-${selected}`"
                class="w-full h-full object-cover object-center animate-fade-in"
                width="300"
                height="600"
            />
            <div
                class="flex w-full absolute left-0 gap-4 items-center justify-center bottom-4"
            >
                <template v-for="n in 3" :key="`button-${n}`">
                    <button
                        class="rounded-lg font-semibold bg-dark-900/30 h-10 p-2 w-10 border-none cursor-pointer hover:bg-dark-900/60 duration-300 hover:text-light-5"
                        @click="setImage(n)"
                    >
                        {{ n }}
                    </button>
                </template>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
const selected = ref(1)
const data = ref([
    {
        index: 1,
        title: 'Project One',
        subtitle: 'Front End Developer',
        description:
            'Nice to meet you. Nice to meet you. Nice to meet you. Nice to meet you. Nice to meet you.'
    },
    {
        index: 2,
        title: 'Project Two',
        subtitle: 'Back End Developer',
        description:
            'Nice to meet you. Nice to meet you. Nice to meet you. Nice to meet you. Nice to meet you.'
    },
    {
        index: 3,
        title: 'Project Three',
        subtitle: 'UI/UX Designer',
        description:
            'Nice to meet you. Nice to meet you. Nice to meet you. Nice to meet you. Nice to meet you.'
    }
])

function setImage(index: number) {
    selected.value = index
}
</script>
