<script setup lang="ts">
</script>

<template>
    <div class="advantages">
        <div class="hero-section">
            <div class="hero-content">
                <div class="text-content">
                    <h1 class="main-title">Агрегатор онлайн-курсов</h1>
                    <p class="description">
                        Сравниваем онлайн-курсы по digital и IT.
                        Мы — каталог-отзовик курсов. Выбирайте курсы по отзывам,
                        цене, продолжительности и другим критериям!
                    </p>
                </div>
                <div class="image-content">
                    <img src="../../public/assets/image.svg" alt="Агрегатор курсов" class="hero-image">
                </div>
            </div>
        </div>

        <h1 class="our">Наши преимущества</h1>
        <div class="advantages-list">
            <div class="foo">
                <div class="icon-title">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-file-play" viewBox="0 0 16 16">
                        <path d="M6 10.117V5.883a.5.5 0 0 1 .757-.429l3.528 2.117a.5.5 0 0 1 0 .858l-3.528 2.117a.5.5 0 0 1-.757-.43z"/>
                        <path d="M4 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h8a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2zm0 1h8a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H4a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1"/>
                    </svg>
                    <h2>Большой выбор
                        <br/>
                        онлайн-курсов
                    </h2>
                </div>
                <p> Мы аккумулируем большое количество
                    онлайн-курсов по различным направлениям,
                    позволяя сравнивать их, и выбирать то,
                    что вам нравится
                </p>
            </div>
            <div class="foo">
                <div class="icon-title">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-search" viewBox="0 0 16 16">
                        <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001q.044.06.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1 1 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0"/>
                    </svg>
                    <h2>
                        Актуальная
                        <br/>
                        информация
                    </h2>
                </div>
                <p>Мы регулярно обновляем наши базы данных,
                    чтобы предоставлять вам только самую свежую информацию
                    о новых курсах, старте обучения, скидках и предложениях от онлайн-школ
                </p>
            </div>
            <div class="foo">
                <div class="icon-title">
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-activity" viewBox="0 0 16 16">
                        <path fill-rule="evenodd" d="M6 2a.5.5 0 0 1 .47.33L10 12.036l1.53-4.208A.5.5 0 0 1 12 7.5h3.5a.5.5 0 0 1 0 1h-3.15l-1.88 5.17a.5.5 0 0 1-.94 0L6 3.964 4.47 8.171A.5.5 0 0 1 4 8.5H.5a.5.5 0 0 1 0-1h3.15l1.88-5.17A.5.5 0 0 1 6 2"/>
                    </svg>
                    <h2>
                        Скорость
                        поиска
                    </h2>
                </div>
                <p> Агрегатор курсов создан для экономии вашего времени.
                    Вы можете с легкостью найти подходящий курс в нашем
                    каталоге по различным фильтрам
                </p>
            </div>
        </div>
    </div>
</template>

<style scoped>
.advantages {
    width: 100%;
    padding: 0;
    margin: 0 auto;
}

.hero-section {
    background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
}

.hero-content {
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    align-items: center;
}

.text-content {
    margin-left: 10%;
    padding-right: 1rem;
}

.main-title {
    font-size: 2.5rem;
    font-weight: 700;
    color: #2c3e50;
    margin-bottom: 1.5rem;
    line-height: 1.2;
}

.description {
    font-size: 1.1rem;
    line-height: 1.6;
    color: #555;
}

.hero-image {
    max-width: 100%;
    height: 100%;
}

.image-content {
    display: flex;
    justify-content: flex-end;
}

.advantages h1 {
    font-size: 2rem;
    font-weight: bold;
    margin: 2rem 0;
}

.our {
    text-align: center;
}

.advantages-list{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 7rem;
}

.foo {
    padding: 2rem;
    width: 300px;
}

.foo img {
    width: 60px;
    height: 60px;
    filter: hue-rotate(90deg) saturate(5);
}

.foo h2 {
    font-size: 1.2rem;
    margin: 1rem 0;
    font-weight: bold;
}

.foo p {
    font-size: 0.95rem;
    color: #555;
}

.icon-title {
    display: flex;
    align-items: center;
    gap: 1rem;
}

.icon-title svg {
    width: 40px;
    height: 40px;
    color: green;
}

/* Responsive design */
@media (max-width: 768px) {
    .hero-content {
        grid-template-columns: 1fr;
        gap: 2rem;
        text-align: center;
    }

    .text-content {
        padding-right: 0;
    }

    .main-title {
        font-size: 2rem;
    }

    .advantages-list {
        gap: 2rem;
    }
}

@media (max-width: 480px) {
    .hero-section {
        padding: 2rem 0;
    }

    .hero-content {
        padding: 0 1rem;
    }

    .main-title {
        font-size: 1.75rem;
    }

    .description {
        font-size: 1rem;
    }
}
</style>