<template>
  <section class="steps">
    <div class="steps__container">
      <!-- Заголовок и описание -->
      <h2 class="steps__title">4 шага работы</h2>
      <p class="steps__subtitle">
        1. Вы присылаете ТЗ и материалы. 2. Я создаю концепт-скицы.
        3. Согласование рендера. 4. Подробная проработка и сдача.
      </p>

      <!-- Карточки -->
      <div class="steps__grid">
        <div
          v-for="(step, index) in steps"
          :key="index"
          class="steps__card"
        >
          <div class="steps__circle">
            <span class="steps__number">{{ index + 1 }}</span>
          </div>
          <h3 class="steps__card-title">{{ step.title }}</h3>
          <p class="steps__card-desc">{{ step.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const steps = [
  {
    title: 'Получение технического задания',
    desc: 'Клиент присылает необходимые чертежи, техническое задание и референсы для работы.'
  },
  {
    title: 'Создание концептуальных набросков',
    desc: 'Разработка основных ракурсов и идей для визуализации.'
  },
  {
    title: 'Согласование чернового рендера',
    desc: 'Обсуждение и корректировка предварительных вариантов визуализации с клиентом.'
  },
  {
    title: 'Детальная проработка и сдача проекта',
    desc: 'Завершение работы над проектом и его передача клиенту.'
  }
];
</script>

<style scoped>
.steps {
  background-color: #3498db;
  padding: 135px 0;
}

.steps__container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.steps__title {
  font-weight: 600;
  font-size: 42px;
  line-height: 1.23;
  color: #ffffff;
  text-align: center;
  margin-bottom: 40px;
}

.steps__subtitle {
  font-weight: 300;
  font-size: 22px;
  line-height: 1.55;
  color: #ffffff;
  text-align: center;
  max-width: 560px;
  margin: 0 auto 120px;
}

/* Сетка: три колонки */
.steps__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

/* Карточка */
.steps__card {
  background-color: #f2f8fd;
  border-radius: 15px;
  padding: 40px 30px;
  text-align: left;          /* ← весь текст выровнен влево */
  transition: transform 0.2s ease;
}

.steps__card:hover {
  transform: translateY(-4px);
}

/* Кружок с номером – прижат к левому краю */
.steps__circle {
  width: 60px;
  height: 60px;
  border: 2px solid #000000;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;       /* убран margin: 0 auto */
}

.steps__number {
  font-weight: 600;
  font-size: 20px;
  line-height: 1;
  color: #000000;
}

/* Заголовок карточки */
.steps__card-title {
  font-weight: 600;
  font-size: 20px;
  line-height: 1.35;
  color: #000000;
  margin-bottom: 12px;
}

/* Описание */
.steps__card-desc {
  font-weight: 300;
  font-size: 16px;
  line-height: 1.55;
  color: #000000;
  opacity: 0.9;
}

/* Адаптивность */
@media screen and (max-width: 960px) {
  .steps__title {
    margin-bottom: 20px;
  }
  .steps__subtitle {
    margin-bottom: 65px;
  }
}

@media screen and (max-width: 640px) {
  .steps {
    padding: 90px 0;
  }
  .steps__title {
    font-size: 30px;
  }
  .steps__subtitle {
    font-size: 18px;
  }
  .steps__grid {
    grid-template-columns: 1fr;
  }
  .steps__card {
    padding: 30px 20px;
  }
}
</style>