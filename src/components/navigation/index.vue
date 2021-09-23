<template>
    <header class="grid grid-cols-6 gap-4 h-8 ">
        <div
            class="bg-contain bg-no-repeat bg-center"
            :style="`background-image: url(${logo});`">
        </div>
        <nav class="col-span-4 h-8 ">
            <list :list="dnav"/>
        </nav>
        <div class="h-8">
            <list :list="dctr" :right="true"/>
        </div>
    </header>
</template>

<script>
    import logo from './../../assets/logo.png'
    import list from './list.vue'
    const gen = (title, list) => ({title, list})
    const name = 'Navigation'
    const components = { list }

    const dnav = [gen('教学'), gen('工具', [gen('MConsole'), gen('ImageCut')]), gen('开源'), gen('博客'), gen('演示')]
    const dctr = [gen('反馈'), gen('关于')]
    const data = () => ({ logo, dnav, dctr })
    const exposed = { name, components, data }
    export default exposed
</script>
