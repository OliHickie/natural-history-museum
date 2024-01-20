<template>
    <div class="container">
        <div class="museum-highlight">
            <img src="" alt="" class="museum-highlight__image">
            <div class="museum-highlight__content">
                <h2 class="museum-highlight__title">
                    {{ data.name }}
                </h2>
                <p class="museum-highlight__description">
                    {{ data.description }}
                </p>
                <PrimaryButton class="museum-highlight__cta">
                    Refresh image
                </PrimaryButton>
            </div>  
        </div>
        <div class="icon">
            <slot name="icon" />
        </div>
    </div>
</template>

<script>
import PrimaryButton from '@/components/Base/PrimaryButton.vue';

export default {
    name: 'MuseumHighlight',
    components: {
        PrimaryButton,
    },
    mixins: [
    ],
    props: {
        data: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {

        };
    },
    computed: {
        newsDate() {
            // Highlight's news item date
        },
    },
    methods: {

    },
    created() {

    },
};
</script>

<style lang="scss" scoped>

.container {
    position: relative;
    .museum-highlight {
        &__image {
            width: 100%;
            aspect-ratio: 3/2;
            background-color: grey;
        }
        &__cta {
            display: block;
            margin: 2rem auto;
        }
    }
    .icon {
        position: absolute;
        top: -24px;
        right: -20px;
    }
}
</style>
