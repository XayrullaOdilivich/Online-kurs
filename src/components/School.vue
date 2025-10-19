<script>
import '@splidejs/vue-splide/css';
import {Splide, SplideSlide} from '@splidejs/vue-splide';

export default {
    name: "CommitPage",
    components: {Splide, SplideSlide},
    data() {
        return {
            perPage: 3,
        };
    },
    methods: {
        prevSlide() {
            this.$refs.splide.go('<');
        },
        nextSlide() {
            this.$refs.splide.go('>');
        },
        updatePerPage() {
            const width = window.innerWidth;
            if (width < 768) {
                this.perPage = 1;
            } else if (width < 1200) {
                this.perPage = 2;
            } else {
                this.perPage = 3;
            }
        },
    },
    mounted() {
        this.updatePerPage();
        window.addEventListener('resize', this.updatePerPage);
    },
    beforeDestroy() {
        window.removeEventListener('resize', this.updatePerPage)
    },
};
</script>


<template>
    <div class="container-fluid">
        <div class="container" data-aos="fade-right">
            <div class="title">Школы</div>
            <Splide
                ref="splide"
                :options="{
                  type: 'loop',
                  autoplay: true,
                  perPage: perPage,
                  perMove: 1,
                  gap: '1rem',
                  arrows: false
                }"
            >
                <SplideSlide>
                    <div class="content">
                       <img alt="img" src="../../public/assets/SkillFactory.png" />
                    </div>
                </SplideSlide>
                <SplideSlide>
                    <div class="content">
                        <img alt="img" src="../../public/assets/otus.png" />
                    </div>
                </SplideSlide>
                <SplideSlide>
                    <div class="content">
                        <img alt="img" src="../../public/assets/geekBrains.png" />
                    </div>
                </SplideSlide>
                <SplideSlide>
                    <div class="content">
                        <div class="netologiya">НЕТОЛОГИЯ</div>
                    </div>
                </SplideSlide>
            </Splide>
            <div class="custom-navigation">
                <button @click="prevSlide"><-</button>
                <button @click="nextSlide">-></button>
            </div>
        </div>
    </div>
</template>

<style scoped>
[data-aos="fade-right"] {
    transition-duration: 3s !important;
}

.container-fluid {
    background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
}

.title {
    color: #2c3e50;
    font-weight: bold;
    text-align: center;
    font-size: 40px;
    margin: 30px;
}

.custom-navigation {
    display: flex;
    justify-content: center;
    margin-top: 10px;
}

.custom-navigation button {
    margin: 0 5px;
    font-size: 30px;
    cursor: pointer;
    background: none;
    color: #555;
    border: none;
}

.content {
    border: blue solid 3px;
    width: 366px;
    height: 294px;
    border-radius: 10px;
    padding: 20px;
    background-color: white;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    overflow: hidden;
    transition: transform 0.9s ease, box-shadow 0.3s ease, background 0.5s ease;
}

.content::before {
    content: "";
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 100%;
    height: 70px;
    background: linear-gradient(to bottom, blue 10%, #2c3e50);
    border-radius: 70px 70px 0 0;
    z-index: 1;
}

.content:hover::before {
    background: linear-gradient(to bottom, deeppink 10%, #1a2e80);
}

.content:hover {
    transform: scale(1.1) rotate(5deg);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.4);
    border-color: deeppink;
}

img {
    width: 200px;
    height: 100px;
    border-radius: 7%;
    border: 3px solid blue;
    transition: border-color 0.3s ease, transform 0.3s ease;
}

.netologiya {
    width: 200px;
    height: 100px;
    border-radius: 7%;
    text-align: center;
    padding: 10%;
    border: 3px solid blue;
    font-weight: bold;
    color: #2c3e50;
    transition: border-color 0.3s ease, transform 0.3s ease;
}

.content:hover img {
    border-color: deeppink;
    transform: scale(1.1);
}

.content:hover .netologiya {
    border-color: deeppink;
    transform: scale(1.1);
}

@media (max-width: 992px) {
    .content {
        width: 90%;
        height: 90%;
    }
}
</style>