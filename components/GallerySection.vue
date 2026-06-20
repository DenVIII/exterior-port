<template>
  <section class="gallery">
    <div class="gallery__container">
      <h2 class="gallery__title">Галерея работ</h2>
      <p class="gallery__subtitle">
        Смотрите примеры: фасады, планы, подсветка, ЖК. При наведении
        изображение увеличивается, при нажатии открывается окно с другими
        изображениями.
      </p>

      <div class="gallery__grid">
        <div
          v-for="project in projects"
          :key="project.id"
          class="gallery__card"
          @click="openProject(project)"
        >
          <div class="gallery__image-wrapper">
            <NuxtImg
                :src="project.mainImage"
                :alt="project.title"
                class="gallery__image"
                sizes="(max-width: 640px) 400px, (max-width: 960px) 600px, 400px"
                loading="lazy"
                format="webp"
            />
            <div class="gallery__overlay"></div>
          </div>
          <div class="gallery__info">
            <span v-if="project.subtitle" class="gallery__uptitle">
              {{ project.subtitle }}
            </span>
            <h3 class="gallery__card-title">{{ project.title }}</h3>
            <p class="gallery__card-desc">{{ project.desc }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    id: 1,
    title: 'Фасад загородного дома',
    subtitle: '',
    desc: 'Реалистичное изображение фасада дома с детализированным отображением материалов.',
    mainImage: '/img/Modern-house-day.Cam010.jpg',
    images: []
  },
  {
    id: 2,
    title: 'Общий план с участком',
    subtitle: '',
    desc: 'Визуализация дома в контексте участка с учётом ландшафта и окружающей среды.',
    mainImage: '/img/site-plan.jpg',
    images: []
  },
  {
    id: 3,
    title: 'Дневная подсветка жилого комплекса',
    subtitle: '',
    desc: 'Изображение ЖК с дневной подсветкой, подчёркивающей архитектурные особенности.',
    mainImage: '/img/daylight-complex.jpg',
    images: []
  },
  {
    id: 4,
    title: 'Вечерняя подсветка коттеджного посёлка',
    subtitle: '',
    desc: 'Визуализация коттеджного посёлка с вечерней подсветкой для создания уютной атмосферы.',
    mainImage: '/img/evening-village.jpg',
    images: []
  },
  {
    id: 5,
    title: 'Общий план ЖК',
    subtitle: 'Жилой комплекс',
    desc: 'Изображение жилого комплекса с детализированным отображением архитектуры и окружения.',
    mainImage: '/img/complex-plan.jpg',
    images: []
  },
  {
    id: 6,
    title: 'Фасад и общий план',
    subtitle: 'Загородный дом',
    desc: 'Комплексная визуализация загородного дома с акцентом на материалы и детали.',
    mainImage: '/img/house-facade-plan.jpg',
    images: []
  }
];

const openProject = (project) => {
  alert(`Открыть проект: ${project.title}`);
};
</script>

<style scoped>
.gallery {
  background-color: #ffffff;
  padding: 135px 0;
}

.gallery__container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.gallery__title {
  font-weight: 600;
  font-size: 42px;
  line-height: 1.23;
  color: #000000;
  text-align: center;
  margin-bottom: 40px;
}

.gallery__subtitle {
  font-weight: 300;
  font-size: 22px;
  line-height: 1.55;
  color: #000000;
  text-align: center;
  max-width: 560px;
  margin: 0 auto 90px;
}

/* Сетка */
.gallery__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 40px 30px;
}

/* Карточка — теперь квадратная */
.gallery__card {
  position: relative;
  aspect-ratio: 1 / 1;       /* квадрат */
  border-radius: 15px;
  overflow: hidden;
  cursor: pointer;
  background-color: #e0e0e0;
}

.gallery__image-wrapper {
  position: absolute;
  inset: 0;
  overflow: hidden;
}

.gallery__image {
  width: 100%;
  height: 100%;
  object-fit: cover;          /* заполняет квадрат, обрезая лишнее */
  transition: transform 0.4s ease;
}

.gallery__card:hover .gallery__image {
  transform: scale(1.05);
}

/* Затемнение */
.gallery__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.1),
    rgba(0, 0, 0, 0.6)
  );
}

/* Текст */
.gallery__info {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 30px 25px 25px;
  color: #ffffff;
  z-index: 1;
}

.gallery__uptitle {
  display: block;
  font-weight: 600;
  font-size: 12px;
  letter-spacing: 2.5px;
  text-transform: uppercase;
  margin-bottom: 5px;
  opacity: 0.9;
}

.gallery__card-title {
  font-weight: 600;
  font-size: 24px;
  line-height: 1.35;
  margin-bottom: 8px;
}

.gallery__card-desc {
  font-weight: 300;
  font-size: 14px;
  line-height: 1.55;
  opacity: 0.9;
}

@media screen and (max-width: 960px) {
  .gallery__grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 30px 20px;
  }
  .gallery__title {
    margin-bottom: 20px;
  }
  .gallery__subtitle {
    margin-bottom: 75px;
  }
}

@media screen and (max-width: 640px) {
  .gallery {
    padding: 90px 0;
  }
  .gallery__title {
    font-size: 30px;
  }
  .gallery__subtitle {
    font-size: 18px;
  }
  .gallery__grid {
    grid-template-columns: 1fr;
    max-width: 400px;
    margin: 0 auto;
  }
}
</style>