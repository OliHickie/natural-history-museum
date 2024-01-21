<template>
    <div class="container">
        <div class="museum-highlight">
            <div  class="museum-highlight__image">
                <img :src="localData.image" :alt="localData.name">
                <div v-if="fetchingImage" class="museum-highlight__image--spinner">
                    <SpinnerIcon class="museum-highlight__image--spinner_icon" />
                </div>
            </div>
            <div :class="['museum-highlight__content', { 'space-partner' : localData.isSpacePartner }]">
                <h2 class="museum-highlight__title">
                    {{ localData.name }}
                </h2>
                <p class="museum-highlight__description">
                    {{ localData.description }}
                </p>
                <article v-if="localData.news" class="museum-highlight__news">
                    <p v-if="localData.news.date" class="museum-highlight__news--date">
                        {{ newsDate }}
                    </p>
                    <p v-if="localData.news.title" class="museum-highlight__news--title">
                        {{ localData.news.title }}
                    </p>
                </article>
                <slot />
                <Button class="museum-highlight__cta" :type="'primary'" @click="getNewImage()">
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
import SpinnerIcon from '@/components/icons/SpinnerIcon.vue';
import { format } from 'date-fns';

export default {
    name: 'MuseumHighlight',
    components: {
        Button,
        SpinnerIcon
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
            localData: { ...this.data },
            fetchingImage: false,
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
        async getNewImage() {
            // Get a new image for the highlight
            this.fetchingImage = true;
            await fetch('newImageAPI').then((response) => {
                if (response.ok) {
                    // this.localData.image = response.data.image;
                    // Mimic a delay
                    setTimeout(() => {
                        this.localData.image = `https://cdn.wccftech.com/wp-content/uploads/2016/09/spacee-scaled.jpg`;
                        this.fetchingImage = false;
                    }, 1000);
                }
            });
        },
    },
};
</script>

<style lang="scss" scoped>

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.container {
    position: relative;
    .museum-highlight {
        &__image {
            width: 100%;
            height: 220px;
            background-color: grey;
            margin: 0;
            padding: 0;
            position: relative;
            & img {
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
            &--spinner {
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%) rotate(0deg);
                &_icon {
                    animation: spin 2s linear infinite;
                    height: 3rem;
                }
            }
        }
        &__content {
            padding: 0.3rem;
            &.space-partner {
                background-color:  rgba(1, 77, 78, 0.3);
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
