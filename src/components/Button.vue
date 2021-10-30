<template>
        <!-- v-on:click="onClick()" -->
        <!-- :click="onClick()" -->
        <!-- @click="onClick()" -->
    <button 
        v-on:click="onClick()"
        :style="{background:color}" 
        class="btn"
    >
        {{text}}
    </button>
</template>

<script>
export default {
    name:"Button",
    props: {
        text: String,
        color: String
    },
    methods: {
        onClick(){
            // console.log("Clicked!")
            this.$emit('toggle-add-task')
        }
    },
    emits:['toggle-add-task']
}
</script>

<style>

</style>