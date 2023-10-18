<script setup>
const neighbours = [
  {
    id: 'usa',
    answer: 'США',
    title: 'Страна № 1',
    questions: [
      {
        id: 1,
        score: 1000,
        text: 'Английского короля Эдуарда VIII, посетившего эту страну в 1957 г., больше всего поразило в ней то, «как родители там слушаются своих детей».'
      },
      {
        id: 2,
        score: 700,
        text: 'Лейбниц назвал эту страну «чистым листом бумаги, на котором можно написать что угодно».'
      },
      {
        id: 3,
        score: 500,
        text: 'По мнению бывшего начальника службы внешней разведки СССР В. Шебаршина, «У русских и ... (жителей этой страны) общая иллюзия — им кажется, что они заслуживают всеобщей любви».'
      },
      {
        id: 4,
        score: 300,
        text: 'Ставшая знаменитой во всем мире фраза «Русские идут» появилась благодаря одному из министров обороны этой страны, который весной 1949 г. бегал по центральным улицам столицы с криком: «Русские идут! Они здесь! Я видел русских солдат!». Он был помещен в военный госпиталь, но выбросился с 16 этажа. Позже его именем был назван авианосец.'
      },
      {
        id: 5,
        score: 100,
        text: 'Рут Маккини утверждает, что «когда поселок в ... (этой стране) превращается в город, событие это бывает отмечено строительством небоскреба».'
      }
    ]
  }
]
</script>
<template>
  <div class="main-container my-grid fill">
    <div class="map-container base-flex"></div>
    <div class="score-container"></div>
    <div class="controls-container"></div>
  </div>
</template>

<style scoped>
.main-container {
  background: rgba(99, 35, 35, 0.493);
  padding: 1% 1% 1.5% 1%;
}
.my-grid {
  display: grid;
  grid-template-columns: 5fr 1fr;
  grid-template-rows: 4fr 1fr;
  gap: 0.1%;
}

.map-container {
  grid-column: 1;
  grid-row: 1;
  background: blue;
}

.score-container {
  grid-column: 2;
  grid-row: 1;
  background: green;
}

.controls-container {
  grid-column: 1/3;
  grid-row: 2;
  background: red;
}
</style>
