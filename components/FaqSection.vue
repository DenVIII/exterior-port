<template>
  <section class="faq">
    <div class="faq__container">
      <h2 class="faq__title">Вопросы и ответы</h2>

      <div class="faq__list">
        <div
          v-for="(item, index) in faqs"
          :key="index"
          class="faq__item"
        >
          <button
            class="faq__header"
            :aria-expanded="item.isOpen"
            @click="toggle(index)"
          >
            <span class="faq__question">{{ item.question }}</span>
            <svg
              class="faq__icon"
              :class="{ 'faq__icon--open': item.isOpen }"
              viewBox="0 0 40 40"
              xmlns="http://www.w3.org/2000/svg"
            >
              <circle cx="20" cy="20" r="20" fill="none" />
              <g stroke="currentColor" stroke-width="2" fill="none">
                <path d="M9 20H31" />
                <path d="M20 9V31" />
              </g>
            </svg>
          </button>
          <div
            :ref="(el) => setContentRef(index, el)"
            class="faq__content"
            :style="item.isOpen ? { maxHeight: contentHeights[index] + 'px' } : { maxHeight: '0' }"
          >
            <div class="faq__text">{{ item.answer }}</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, nextTick } from 'vue'

const faqs = ref([
  {
    question: 'Какие исходные данные необходимы для работы?',
    answer: 'Чертежи, планы фасадов, разрезы.',
    isOpen: false
  },
  {
    question: 'Какова стоимость услуг?',
    answer: 'Зависит от сложности и количества ракурсов.',
    isOpen: false
  },
  {
    question: 'Какие сроки выполнения работ?',
    answer: 'От 3 до 10 дней на объект.',
    isOpen: false
  },
  {
    question: 'С кем вы работаете?',
    answer: 'С архитекторами, строительными компаниями и частными заказчиками.',
    isOpen: false
  }
])

const contentElements = ref([])
const contentHeights = ref([])

// Сохраняем ссылки на DOM-элементы контента
const setContentRef = (index, el) => {
  if (el) contentElements.value[index] = el
}

const toggle = async (index) => {
  const item = faqs.value[index]
  item.isOpen = !item.isOpen

  // После изменения состояния дожидаемся перерисовки, затем измеряем высоту
  await nextTick()
  const el = contentElements.value[index]
  if (el) {
    contentHeights.value[index] = el.scrollHeight
  }
}
</script>

<style scoped>
.faq {
  background-color: #f2f8fd;
  padding: 135px 0;
}

.faq__container {
  max-width: 960px;
  margin: 0 auto;
  padding: 0 20px;
}

.faq__title {
  font-weight: 600;
  font-size: 42px;
  line-height: 1.23;
  color: #000000;
  text-align: center;
  margin-bottom: 90px;
}

/* Список */
.faq__list {
  display: flex;
  flex-direction: column;
}

/* Элемент списка */
.faq__item {
  border-top: 1px solid rgba(0, 0, 0, 0.5);
}

.faq__item:last-child {
  border-bottom: 1px solid rgba(0, 0, 0, 0.5);
}

/* Кнопка-заголовок */
.faq__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 24px 0;
  background: none;
  border: none;
  cursor: pointer;
  text-align: left;
}

.faq__question {
  font-weight: 600;
  font-size: 22px;
  line-height: 1.35;
  color: #000000;
  padding-right: 20px;
}

/* Иконка */
.faq__icon {
  width: 40px;
  height: 40px;
  flex-shrink: 0;
  color: #000000;
  transition: transform 0.3s ease;
}

/* Поворот на 45° – плюс становится крестиком */
.faq__icon--open {
  transform: rotate(45deg);
}

/* Контент */
.faq__content {
  overflow: hidden;
  transition: max-height 0.3s ease;
  will-change: max-height;
}

.faq__text {
  font-weight: 300;
  font-size: 18px;
  line-height: 1.55;
  color: #000000;
  padding-bottom: 24px;
}

/* Адаптив */
@media screen and (max-width: 960px) {
  .faq__title {
    margin-bottom: 45px;
  }
}

@media screen and (max-width: 640px) {
  .faq {
    padding: 90px 0;
  }
  .faq__title {
    font-size: 30px;
  }
  .faq__question {
    font-size: 18px;
  }
  .faq__icon {
    width: 32px;
    height: 32px;
  }
}
</style>