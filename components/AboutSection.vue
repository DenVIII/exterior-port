<template>
  <section class="about">
    <div class="about__container">
      <!-- Левая колонка: текст -->
      <div class="about__text-col">
        <h2 class="about__title">Кристина</h2>
        <p class="about__subtitle">Визуализатор</p>
        <div class="about__divider"></div>
        <p class="about__description">
          О специалисте: Визуализатор. Имеет глубокие знания в области дизайна,
          материалов и освещения.
        </p>
      </div>

      <!-- Правая колонка: фото -->
      <div class="about__img-col">
        <div class="about__img"></div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* ===== Секция ===== */
.about {
  background-color: #f2f8fd;
  padding: 135px 0;
}

.about__container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  align-items: center;
  gap: 60px;
}

/* ----- Левая колонка ----- */
.about__text-col {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.about__title {
  font-family: 'TildaSans', Arial, sans-serif;
  font-weight: 600;
  font-size: 42px;
  line-height: 1.23;
  color: #000000;
  margin-bottom: 10px;
}

.about__subtitle {
  font-family: 'TildaSans', Arial, sans-serif;
  font-weight: 300;
  font-size: 22px;
  line-height: 1.55;
  color: #000000;
  margin-bottom: 20px;
}

.about__divider {
  width: 100%;
  height: 2px;
  background-color: #3498db;
  margin-bottom: 20px;
}

.about__description {
  font-family: 'TildaSans', Arial, sans-serif;
  font-weight: 300;
  font-size: 18px;
  line-height: 1.55;
  color: #000000;
}

/* ----- Правая колонка ----- */
.about__img-col {
  flex: 1;
}

.about__img {
  width: 100%;
  height: 560px;
  background: url('/img/about-photo.png') center/cover no-repeat;
  background-color: #e0e0e0; /* запасной цвет, пока фото не загрузится */
  border-radius: 15px;
}

/* ----- Адаптация для мобильных ----- */
@media screen and (max-width: 960px) {
  .about__container {
    flex-direction: column;
    text-align: center;
  }
  .about__text-col,
  .about__img-col {
    width: 100%;
  }
  .about__img {
    height: 400px;
  }
}

@media screen and (max-width: 640px) {
  .about {
    padding: 90px 0;
  }
  .about__title {
    font-size: 30px;
  }
  .about__subtitle {
    font-size: 18px;
  }
  .about__description {
    font-size: 16px;
  }
}
</style>