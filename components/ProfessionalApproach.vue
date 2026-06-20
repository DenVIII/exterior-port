<template>
  <section class="professional">
    <div class="professional__container">
      <!-- Заголовок и описание -->
      <h2 class="professional__title">Профессиональный подход</h2>
      <p class="professional__subtitle">
        Читаю чертежи, знаю конструкции. Создаю визуализации с ландшафтом,
        светом и тенями. Помогаю выбирать материалы и варианты отделки фасада.
        Работаю под ключ: от чертежей до финального рендера.
      </p>

      <!-- Сетка преимуществ -->
      <div class="professional__grid">
        <div
          v-for="item in advantages"
          :key="item.title"
          class="professional__card"
        >
          <div class="professional__icon-wrapper">
            <svg
              class="professional__icon"
              viewBox="0 0 32 32"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <circle cx="16" cy="16" r="15" fill="#3498db" />
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M24.714 11.557L23.224 10.13 13.64 20.15l-4.41-4.41-1.46 1.458 5.902 5.902 11.042-11.543z"
                fill="white"
              />
            </svg>
          </div>
          <div class="professional__text">
            <h3 class="professional__item-title">{{ item.title }}</h3>
            <p class="professional__item-desc">{{ item.desc }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const advantages = [
  {
    title: 'Чтение чертежей',
    desc: 'Глубокое понимание архитектурных проектов благодаря чтению чертежей.'
  },
  {
    title: 'Знание конструкций',
    desc: 'Детальное знание строительных конструкций для точного воспроизведения в визуализации.'
  },
  {
    title: 'Живые визуализации',
    desc: 'Проработка ландшафта, света и теней для создания реалистичной атмосферы.'
  },
  {
    title: 'Помощь с материалами',
    desc: 'Показ различных вариантов отделки фасада для выбора оптимальных материалов.'
  },
  {
    title: 'Работа под ключ',
    desc: 'Комплексный подход: от изучения чертежей до финального рендера.'
  }
];
</script>

<style scoped>
.professional {
  background-color: #ffffff;
  padding: 135px 0;
}

.professional__container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.professional__title {
  font-family: 'TildaSans', Arial, sans-serif;
  font-weight: 600;
  font-size: 42px;
  line-height: 1.23;
  color: #000000;
  text-align: center;
  margin-bottom: 40px;
}

.professional__subtitle {
  font-family: 'TildaSans', Arial, sans-serif;
  font-weight: 300;
  font-size: 22px;
  line-height: 1.55;
  color: #000000;
  text-align: center;
  max-width: 560px;
  margin: 0 auto 90px;
}

.professional__grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 40px 60px;
}

.professional__card {
  display: flex;
  align-items: flex-start;
  gap: 20px;
}

.professional__icon-wrapper {
  flex-shrink: 0;
  width: 30px;
  height: 30px;
}

.professional__icon {
  width: 100%;
  height: 100%;
  display: block;
}

.professional__item-title {
  font-family: 'TildaSans', Arial, sans-serif;
  font-weight: 600;
  font-size: 20px;
  line-height: 1.35;
  color: #000000;
  margin-top: 0;
  margin-bottom: 0;
}

.professional__item-desc {
  font-family: 'TildaSans', Arial, sans-serif;
  font-weight: 300;
  font-size: 16px;
  line-height: 1.55;
  color: #000000;
}

@media screen and (max-width: 960px) {
  .professional__title {
    margin-bottom: 20px;
  }
  .professional__subtitle {
    margin-bottom: 45px;
  }
  .professional__grid {
    grid-template-columns: 1fr;
    gap: 30px;
  }
}

@media screen and (max-width: 640px) {
  .professional {
    padding: 90px 0;
  }
  .professional__title {
    font-size: 30px;
  }
  .professional__subtitle {
    font-size: 18px;
  }
  .professional__item-title {
    font-size: 18px;
  }
}
</style>