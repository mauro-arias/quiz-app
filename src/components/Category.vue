<template>
    <div @click='changeCategory' :class='[isSelected ? "border-2 border-green-500" : "border-2 border-transparent","card", "p-3", "mt-5", "mx-5", "flex", "justify-center", "flex-wrap", "w-80", "cursor-pointer", "hover:-translate-y-1", "transform", "ease-in", "duration-100"]'>
        <div class='flex justify-center items-center flex-col'>
            <img class='h-64' :src="require(`../assets/img/${img}`)" :alt="img">
            <p class='text-center w-full font-medium block'>{{ name }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Category',
    props: {
        name: String,
        img: String,
        isSelected: Boolean
    },
    methods: {
        changeCategory(){
            this.$store.state.category = this.name;
        }
    }
}
</script>