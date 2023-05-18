<template>
    <div
        class="flex flex-col w-full px-4 gap-4 lg:px-8 mx-auto xl:px-0 xl:w-3/4"
    >
        <div class="flex flex-col gap-2">
            <h2 class="text-light-50/80 font-100 pt-2 text-4">
                <slot name="subtitle" />
            </h2>
            <h1 class="font-semibold text-3xl text-light-50 lg:text-6xl">
                <slot name="title" />
            </h1>
        </div>
        <p class="font-normal text-base text-light-50/60 lg:text-lg pt-5">
            <slot name="description" />
        </p>
        <nav class="flex gap-4 pt-5">
            <slot name="projectLink" />
        </nav>
    </div>
</template>
