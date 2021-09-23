<template>
    <ul class="flex flex-row h-full px-8 text-gray-900" :class="{ 'justify-end': right }">
        <li
            class="nav-item whitespace-nowrap px-8 flex items-center h-full cursor-pointer relative hover:text-white hover:bg-gray-600"
            v-for="(term, index) in list"
            @click="menuItemHandle(term)"
            :key="index"
        >
            {{ term.title }}
            <ul
                v-if="Object.prototype.toString(term) == '[object Object]'"
                class="absolute top-8 left-0 hidden text-gray-900 shadow-lg"
            >
                <li class="h-2 w-full"></li>
                <li
                    v-for="(sublTerm, sublIndex) in term.list"
                    :key="sublIndex"
                    class="bg-gray-300 hover:text-white hover:bg-gray-400 px-8 py-2 whitespace-nowrap"
                    @click="menuItemHandle(sublTerm)"
                >{{ sublTerm.title }}</li>
            </ul>
        </li>
    </ul>
</template>

<script>
const props = ['list', 'right']
const emits = ['selected']
const setup = (_, context) => {
    const menuItemHandle = data => context.emit('selected', data)
    return { menuItemHandle }
}
const exposed = { props, emits, setup }
export default exposed
</script>

<style scoped>
.nav-item:hover ul {
    display: block;
}
</style>
