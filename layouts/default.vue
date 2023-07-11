<template>
    <div>
        <!-- A *default* layout -->
        <slot />
    </div>
</template>
<style lang="scss" scoped>
    div {
        background: $blue-900;
        color: #ffffff;
        min-height: 100vh;
    }
</style>