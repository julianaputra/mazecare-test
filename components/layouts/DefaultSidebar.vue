<template>
    <div>
        <div>
            [logo]
        </div>
        <nav>
            <NuxtLink :to="{name: 'index'}">[home]</NuxtLink>
            <NuxtLink :to="{name: 'index'}">[theme]</NuxtLink>
            <NuxtLink :to="{name: 'index'}">[folders]</NuxtLink>
            <NuxtLink :to="{name: 'index'}">[schedules]</NuxtLink>
            <NuxtLink :to="{name: 'index'}">[files]</NuxtLink>
            <NuxtLink :to="{name: 'index'}">[report]</NuxtLink>
        </nav>
        <div>
            <button>[toggle]</button>
            <button>[setting]</button>
        </div>
    </div>
</template>