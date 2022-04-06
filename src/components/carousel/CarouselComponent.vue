<template>
    <div class="carousel">
        <slot></slot>
        <button class="carousel__nav carousel__next" @click.prevent="next">Suivante</button>
        <button class="carousel__nav carousel__prev" @click.prevent="previous">Précedente</button>
    </div>
</template>

<script>
export default {
    data() {

        return {
            index: 0,
            slides: [],
        }
    },
    mounted() {
        this.slides = this.$children;
        this.slides.forEach((slide, i) => {
            slide.index = i
        })
    },
    computed: {
        slidesCount() { return this.slides.length }
    },
    methods: {
        next() {
            this.index++;
            if(this.index >= this.slidesCount ) this.index = 0;
        },
        previous() {
            this.index--;
            if(this.index < 0) this.index = this.slidesCount-1;
        }
    }
}
</script>