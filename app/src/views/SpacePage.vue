<template>
    <div class="space-page">

        <h1 class="space-page__title">
            Space
        </h1>
        <div class="highlights">
            <div v-for="(highlight, index) in highlightData" :key="index" class="highlights__highlight">
                <MuseumHighlight :data="highlight">
                    <a v-if="highlight.quiz" :href="highlight.quiz" target="_blank" class="highlights__highlight--quiz">
                        Take our quiz
                        <ChevronRight class="highlights__highlight--quiz_icon" />
                    </a>
                    <template v-slot:icon>
                        <StarIcon class="highlight-icon" />
                    </template>
                </MuseumHighlight>
            </div>
        </div>
        <!-- Add the museum highlight cards based on the data provided below -->

    </div>
</template>

<script>
import StarIcon from '@/components/icons/StarIcon.vue';
import ChevronRight from '@/components/icons/ChevronRight.vue';
import MuseumHighlight from './MuseumHighlight.vue';

export default {
    name: 'SpacePage',
    components: {
        MuseumHighlight,
        StarIcon,
        ChevronRight
    },
    mixins: [
    ],
    props: {

    },
    data() {
        return {
            spaceHighlights: [
                {
                    date: '2020-04-20 12:20:00',
                    description: 'Asteroids are minor planets, especially of the inner Solar System. Larger asteroids have also been called planetoids.',
                    id: 1,
                    image: 'https://science.nasa.gov/wp-content/uploads/2023/08/psyche-asteroid-illustration-pia24472.jpg',
                    name: 'Asteroids',
                },
                {
                    date: '2020-05-20 15:50:00',
                    description: 'A comet is an icy, small Solar System body that, when passing close to the Sun, warms and begins to release gases, a process called outgassing.',
                    id: 9,
                    image: 'https://www.usatoday.com/gcdn/presto/2020/07/16/USAT/f2c1c588-335e-4d1b-a1d5-204699ca8bd3-AP_APTOPIX_Oregon_Comet_Neowise.jpg?crop=4777,2687,x0,y606&width=3200&height=1800&format=pjpg&auto=webp',
                    name: 'Comets',
                },
                {
                    date: '2020-05-01 9:22:00',
                    description: 'The term planet is ancient, with ties to history, astrology, science, mythology, and religion.',
                    id: 7,
                    image: 'https://media.istockphoto.com/id/182910299/photo/the-solar-system-in-a-line.jpg?s=612x612&w=0&k=20&c=prHWrLZtqfzL9NJXvJ_aI-gU__TKS7pXkdCSqR3cWJc=',
                    name: 'Planets',
                    news: {
                        date: '2020-08-18 18:00:00',
                        title: 'Attend our talk about Jupiter with Dr. Hogarth',
                    },
                    quiz: 'https://planetquiz.space',
                },
                {
                    date: '2020-07-05 4:10:00',
                    description: 'A meteor shower is a celestial event in which a number of meteors are observed to radiate, or originate, from one point in the night sky.',
                    id: 12,
                    image: 'https://imageio.forbes.com/specials-images/imageserve/656bb721a5f8602a7b456f04/Star-shower/960x0.jpg?format=jpg&width=960',
                    name: 'Meteor showers',
                    news: {
                        title: 'The Lyrids will peak at on April 21-22 2021, at night',
                    },
                },
            ],
            spacePartners: {
                observatory: {
                    createdAt: '2020-06-01 11:45:00',
                    info: 'The Mauna Kea Observatories (MKO) are a number of independent astronomical research facilities and large telescope observatories that are located at the summit of Mauna Kea on the Big Island of Hawaiʻi, United States.',
                    image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Mauna_Kea_Summit_2021-06-16_33_%28cropped%29.jpg/640px-Mauna_Kea_Summit_2021-06-16_33_%28cropped%29.jpg',
                    name: 'Mauna Kea Observatories',
                },
            },
        };
    },
    computed: {
        highlightData() {
            let data = [...this.spaceHighlights];

            if (this.spacePartners) {
                for (const key in this.spacePartners) {
                    const element = this.spacePartners[key];
                    data.push({
                        date: element.createdAt,
                        description: element.info,
                        image: element.image,
                        name: element.name,
                        isSpacePartner: true,
                    });
                }
            }
            // Sort data by date
            data.sort((a, b) => {
                return new Date(b.date) - new Date(a.date);
            });
            return data;
        }

    },
};
</script>

<style lang="scss" scoped>
.space-page {
    max-width: 1500px;
    margin: 0 auto;
    &__title {
        font-size: 2.5rem;
        margin: 2rem 0 0 2rem;
        font-weight: 300;
    }
}

.highlights {
    display: grid;
    @media (min-width: 768px) {
        grid-template-columns: repeat(2, 1fr);
    }
    @media (min-width: 1024px) {
        grid-template-columns: repeat(3, 1fr);
    }
    @media (min-width: 1300px) {
        grid-template-columns: repeat(4, 1fr);
    }

    &__highlight {
        padding: 2rem;
        &--quiz {
            color: #000;
            display: inline-block;
            margin-top: 1rem;
            font-weight: 500;
            padding: 0.5rem;
            border-radius: 0.5rem;
            line-height: 1;
            &:hover {
                background-color: #EDEDED;
            }
            &_icon {
                height: 1rem;
                width: 1rem;
                margin-left: 0.5rem;
                vertical-align: middle;            
            }
        }
    }
}

.highlight-icon {
    display: block;
    height: 3rem;
    width: 3rem
}
</style>
