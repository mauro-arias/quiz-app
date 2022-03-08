<template>
    <button class='px-5 py-2 text-lg'><i :class="`${icon} mr-1`"></i> {{ text }}</button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String,
        icon: String
    },

}
</script>