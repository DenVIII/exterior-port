<template>
  <section class="hero">
    <!-- Обычный img, фон -->
    <img
      src="/img/hero-bg.jpg"
      class="hero__bg"
      alt="Фон визуализации"
    />
    <!-- Затемнение -->
    <div class="hero__overlay"></div>
    <!-- Контент -->
    <div class="hero__content">
      <h1 class="hero__title">Оживите ваш проект до стройки</h1>
      <p class="hero__descr">
        Создайте фон с эффектной визуализацией современного коттеджа. 
        Фотореалистичные 3D‑изображения частных домов, коттеджей и ЖК. 
        Рассчитайте стоимость визуализации, нажав на кнопку.
      </p>
      <a href="#contact" class="hero__btn">Рассчитать стоимость</a>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  height: 90vh;
  min-height: 600px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 20px;
  overflow: hidden;
}

.hero__bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 0;
}

.hero__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(rgba(51, 36, 0, 0.6), rgba(0, 0, 0, 0.6));
  z-index: 1;
}

.hero__content {
  position: relative;
  z-index: 2;
  width: 100%;
  max-width: 960px;
  margin: 0 auto;
  padding: 0 20px;
  text-align: center;
  color: #ffffff;
}

.hero__title {
  font-weight: 600;
  font-size: 52px;
  line-height: 1.23;
  margin-bottom: 20px;
}

.hero__descr {
  font-weight: 300;
  font-size: 22px;
  line-height: 1.55;
  margin-bottom: 30px;
  opacity: 0.9;
}

.hero__btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 60px;
  padding: 0 60px;
  font-weight: 600;
  font-size: 16px;
  color: #ffffff;
  background-color: #3498db;
  border-radius: 32px;
  text-decoration: none;
  transition: background-color 0.2s ease;
}

.hero__btn:hover {
  background-color: #2c81ba;
}

@media screen and (max-width: 640px) {
  .hero {
    height: auto;
    padding: 60px 0;
  }
  .hero__title {
    font-size: 32px;
  }
  .hero__descr {
    font-size: 16px;
  }
  .hero__btn {
    height: 50px;
    padding: 0 40px;
    font-size: 14px;
  }
}
</style>