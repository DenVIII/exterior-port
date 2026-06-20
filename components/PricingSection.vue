<template>
  <section class="pricing">
    <div class="pricing__container">
      <!-- Заголовок и описание -->
      <h2 class="pricing__title">Стоимость услуг</h2>
      <p class="pricing__subtitle">
        Коттеджи (до 150 м²): от 9 000 ₽. Дома (от 150 м²): от 14 000 ₽.
        Жилые комплексы: от 20 000 ₽. Цена зависит от сложности и обсуждается индивидуально.
      </p>

      <!-- Карточки -->
      <div class="pricing__grid">
        <div
          v-for="plan in plans"
          :key="plan.title"
          class="pricing__card"
        >
          <h3 class="pricing__card-title">
            <template v-if="plan.title.includes('(')">
              {{ plan.title.split('(')[0].trim() }}<br />
              ({{ plan.title.split('(')[1] }}
            </template>
            <template v-else>
              {{ plan.title }}
            </template>
          </h3>
          <div class="pricing__price">{{ plan.price }}</div>
          <p class="pricing__card-desc">{{ plan.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const plans = [
  {
    title: 'Небольшие коттеджи (до 150 м²)',
    price: '9 000 ₽',
    desc: 'Создание фотореалистичного 3D-изображения экстерьера, визуализация объекта в связке с ландшафтом'
  },
  {
    title: 'Большие частные дома (от 150 м²)',
    price: '14 000 ₽',
    desc: 'Создание фотореалистичного 3D-изображения экстерьера, визуализация объекта в связке с ландшафтом'
  },
  {
    title: 'Жилые комплексы',
    price: '20 000 ₽',
    desc: 'Создание фотореалистичного 3D-изображения экстерьера, визуализация объекта в связке с ландшафтом'
  }
];
</script>

<style scoped>
.pricing {
  background-color: #ffffff;
  padding: 135px 0;
}

.pricing__container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.pricing__title {
  font-weight: 600;
  font-size: 42px;
  line-height: 1.23;
  color: #000000;
  text-align: center;
  margin-bottom: 40px;
}

.pricing__subtitle {
  font-weight: 300;
  font-size: 22px;
  line-height: 1.55;
  color: #000000;
  text-align: center;
  max-width: 560px;
  margin: 0 auto 105px;
}

/* Сетка */
.pricing__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

/* Карточка */
.pricing__card {
  background-color: #ffffff;
  border: 1px solid rgba(0, 0, 0, 0.5);
  border-radius: 15px;
  padding: 40px 30px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.pricing__card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
}

.pricing__card-title {
  font-weight: 600;
  font-size: 22px;
  line-height: 1.35;
  color: #000000;
  margin-bottom: 20px;
}

.pricing__price {
  font-weight: 600;
  font-size: 42px;
  line-height: 1.23;
  color: #3498db;
  margin-bottom: 20px;
}

.pricing__card-desc {
  font-weight: 300;
  font-size: 16px;
  line-height: 1.55;
  color: #000000;
  opacity: 0.9;
}

/* Адаптивность */
@media screen and (max-width: 960px) {
  .pricing__grid {
    grid-template-columns: 1fr;
    gap: 25px;
  }
  .pricing__title {
    margin-bottom: 20px;
  }
  .pricing__subtitle {
    margin-bottom: 30px;
  }
}

@media screen and (max-width: 640px) {
  .pricing {
    padding: 90px 0;
  }
  .pricing__title {
    font-size: 30px;
  }
  .pricing__subtitle {
    font-size: 18px;
  }
  .pricing__card {
    padding: 30px 20px;
  }
  .pricing__price {
    font-size: 32px;
  }
}
</style>