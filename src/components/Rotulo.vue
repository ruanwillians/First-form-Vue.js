<template>
    <div class="rotulo">
        <label>{{ name }}:</label>
        <div class="elemento">
            <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
    props: ['name']
}
</script>

<style scoped>
    .rotulo {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        margin: 15px 0px;
        font-size: 1.4rem;
    }

    .elemento {
        display: flex;
        align-self: stretch;
    }


</style>
