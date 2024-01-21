<template>
    <div class="container">
        <div class="museum-highlight">
            <img src="" alt="" class="museum-highlight__image">
            <div :class="['museum-highlight__content', { 'space-partner' : data.isSpacePartner }]">
                <h2 class="museum-highlight__title">
                    {{ data.name }}
                </h2>
                <p class="museum-highlight__description">
                    {{ data.description }}
                </p>
                <article v-if="data.news" class="museum-highlight__news">
                    <p v-if="data.news.date" class="museum-highlight__news--date">
                        {{ newsDate }}
                    </p>
                    <p v-if="data.news.title" class="museum-highlight__news--title">
                        {{ data.news.title }}
                    </p>
                </article>
                <slot />
                <Button class="museum-highlight__cta" :type="'primary'">
                    Refresh image
                </Button>
            </div>  
        </div>
        <div class="icon">
            <slot name="icon" />
        </div>
    </div>
</template>

<script>
import Button from '@/components/Base/Button.vue';
import { format } from 'date-fns';

export default {
    name: 'MuseumHighlight',
    components: {
        Button,
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
            const date = new Date(this.data.news.date);
            return format(date, 'do MMM yyyy, HH:mm');
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
        &__content {
            padding: 0.3rem;
            &.space-partner {
                background-color:  rgba(1, 77, 78, 0.4);
            }
        }
        &__news {
            font-size: 0.8rem;
            margin-top: 1rem;
            border-top: 1px solid rgba(0, 0, 0, 0.2);
            &--date {
                font-weight: 600;
            }
            &--title {
                font-weight: 600;
            }
        }
        &__cta {
            display: block;
            margin: 2rem auto 0;
        }
    }
    .icon {
        position: absolute;
        top: -24px;
        right: -20px;
    }
}
</style>
