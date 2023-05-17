<template>
    <div
        class="flex flex-col mx-auto w-full px-4 gap-4 lg:px-8 xl:px-0 xl:w-3/4"
    >
        <div class="flex flex-col gap-2">
            <h1 class="font-semibold text-3xl text-light-50 lg:text-6xl">
                <slot name="title" />
            </h1>
            <h2 class="font-medium text-xl text-light-50/80 lg:text-3xl">
                <slot name="subtitle" />
            </h2>
        </div>
        <p class="'font-normal text-base text-light-50/60 lg:text-lg">
            <slot name="description" />
        </p>
        <nav class="flex gap-4">
            <NuxtLink
                class="font-normal text-base text-light-50/60 inline-block underline"
            >
                Instagram
            </NuxtLink>
            <NuxtLink
                class="font-normal text-base text-light-50/60 inline-block underline"
            >
                Twitter
            </NuxtLink>
        </nav>
    </div>
</template>
