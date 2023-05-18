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
                    <template #projectLink>
                        <a
                            :href="_d.projectLink"
                            target="_blank"
                            class="font-normal text-base text-light-5 cursor-pointer duration-300 rounded-1 p-2 outline outline-1 hover:bg-light-5 hover:text-dark duration-500 no-underline"
                        >
                            ⇢ {{ _d.projectLink }}
                        </a>
                    </template>
                </PhotoInfo>
            </template>
        </div>
        <div class="h-screen w-full relative lg:w-1/2">
            <img
                :src="useAsset(`photos_${selected}` + '.jpg')"
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
                        class="p-2 cursor-pointer duration-300 text-light-5 rounded-lg font-semibold bg-dark-900/70 h-10 w-10 border-none hover:bg-dark-900/50"
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
        title: 'Shuyuan’s Portfolio',
        subtitle: '#React #SASS #NPM #Sanity',
        description: '用一頁式網頁介紹自己及專案紀錄。',
        projectLink: 'https://shuyuanchuang.com'
    },
    {
        index: 2,
        title: 'iOS Club',
        subtitle: '#React #Tailwindcss #Figma',
        description:
            '在擔任 iOS Club 副社長期間，與社團夥伴共同開發的社團網頁用於介紹與招生。',
        projectLink: 'https://iosclub.tw/'
    },
    {
        index: 3,
        title: 'Save Food Battle',
        subtitle: '#Flutter #MongoDB #Figma #Firebase #Figma',
        description:
            '為減少食物浪費及室友間的和諧，本專題計畫為發展出一個完善的多人食材管理系統為主，並利用自動化功能計算食品到期日、減少繁瑣輸入資料的步驟、使用影像辨識及 AR 技術分辨食物的持有人、食物種類等，以有別於市面上的方式，讓使用者追求更佳完善的使用者體驗。',
        projectLink: 'https://github.com/FOR-Shu/Save_food_Battle'
    }
])

function setImage(index: number) {
    selected.value = index
}

function useAsset(path: string): string {
    const assets = import.meta.glob('~/assets/**/*', {
        eager: true,
        import: 'default'
    })
    // @ts-expect-error: wrong type info
    return assets['/assets/' + path]
}
</script>
