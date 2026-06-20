<template>
  <section class="services">
    <div class="services__container">
      <!-- Заголовок и описание -->
      <h2 class="services__title">Услуги</h2>
      <p class="services__subtitle">
        Предлагаю услуги по визуализации частных домов и коттеджей, жилых
        комплексов, а также ландшафтов (интеграция дома в участок).
      </p>

      <!-- Сетка услуг -->
      <div class="services__grid">
        <div
          v-for="service in services"
          :key="service.id"
          class="services__card"
        >
          <div class="services__image-wrapper">
            <NuxtImg
              :src="service.image"
              :alt="service.title"
              class="services__image"
              format="webp"
              sizes="(max-width: 640px) 100vw, (max-width: 960px) 50vw, 600px"
              loading="lazy"
            />
          </div>
          <div class="services__text">
            <h3 class="services__card-title">{{ service.title }}</h3>
            <p class="services__card-desc">{{ service.desc }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const services = [
  {
    id: 1,
    title: 'Визуализация частных домов и коттеджей',
    desc: 'Создание детальных 3D-моделей частных домов и коттеджей для демонстрации на стадии идеи.',
    image: '/img/service-houses.jpg'
  },
  {
    id: 2,
    title: 'Визуализация жилых комплексов',
    desc: 'Разработка фотореалистичных изображений жилых комплексов для презентации потенциальным инвесторам и покупателям.',
    image: '/img/service-complex.jpg'
  },
  {
    id: 3,
    title: 'Визуализация ландшафта',
    desc: 'Создание 3D-моделей, демонстрирующих интеграцию дома в ландшафт участка для демонстрации потенциальным клиентам.',
    image: '/img/service-landscape.jpg'
  },
  {
    id: 4,
    title: 'Архитектурная визуализация',
    desc: 'Предоставление фотореалистичных изображений для архитектурных проектов.',
    image: '/img/service-architecture.jpg'
  }
];
</script>

<style scoped>
.services {
  background-color: #f2f8fd;
  padding: 135px 0;
}

.services__container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.services__title {
  font-weight: 600;
  font-size: 42px;
  line-height: 1.23;
  color: #000000;
  text-align: center;
  margin-bottom: 40px;
}

.services__subtitle {
  font-weight: 300;
  font-size: 22px;
  line-height: 1.55;
  color: #000000;
  text-align: center;
  max-width: 560px;
  margin: 0 auto 90px;
}

/* Сетка: 2 колонки */
.services__grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 40px 30px;
}

/* Карточка */
.services__card {
  background: #ffffff;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 4px 20px rgba(0,0,0,0.05);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.services__card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 30px rgba(0,0,0,0.1);
}

/* Обёртка изображения с заданным соотношением */
.services__image-wrapper {
  width: 100%;
  aspect-ratio: 700 / 425;  /* ≈ 60.7% высоты от ширины, как в оригинале */
  overflow: hidden;
  background-color: #e0e0e0;
}

.services__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* Текстовая часть */
.services__text {
  padding: 30px 25px;
}

.services__card-title {
  font-weight: 600;
  font-size: 22px;
  line-height: 1.35;
  color: #000000;
  margin-bottom: 10px;
}

.services__card-desc {
  font-weight: 300;
  font-size: 16px;
  line-height: 1.55;
  color: #000000;
  opacity: 0.9;
}

/* Адаптивность */
@media screen and (max-width: 960px) {
  .services__title {
    margin-bottom: 20px;
  }
  .services__subtitle {
    margin-bottom: 45px;
  }
}

@media screen and (max-width: 640px) {
  .services {
    padding: 90px 0;
  }
  .services__title {
    font-size: 30px;
  }
  .services__subtitle {
    font-size: 18px;
  }
  .services__grid {
    grid-template-columns: 1fr;
  }
  .services__card-title {
    font-size: 20px;
  }
}
</style>