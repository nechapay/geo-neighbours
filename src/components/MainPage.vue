<script setup>
import { ref, reactive, watch } from 'vue'
import QuestionViewer from './QuestionViewer.vue'
import RFMap from './RFMap.vue'
import gsap from 'gsap'

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
const teams = ref([
  {
    id: 1,
    name: 'Команда 1',
    score: 0
  },
  {
    id: 1,
    name: 'Команда 2',
    score: 0
  },
  {
    id: 1,
    name: 'Команда 3',
    score: 0
  },
  {
    id: 1,
    name: 'Команда 4',
    score: 0
  }
])

const animatedScore1 = reactive({
  number: 0
})

const score1 = ref(0)

const animatedScore2 = reactive({
  number: 0
})

const score2 = ref(0)

const animatedScore3 = reactive({
  number: 0
})

const score3 = ref(0)

const animatedScore4 = reactive({
  number: 0
})

const score4 = ref(0)

let dialogVisible = ref(false)
let index = ref(0)

function handleUpdateScore(team, idx) {
  teams.value[team].score += neighbours[index.value].questions[idx].score
  switch (team) {
    case 0:
      score1.value += neighbours[index.value].questions[idx].score
      break
    case 1:
      score2.value += neighbours[index.value].questions[idx].score
      break
    case 2:
      score3.value += neighbours[index.value].questions[idx].score
      break
    case 3:
      score4.value += neighbours[index.value].questions[idx].score
      break
    default:
      break
  }
}

watch(score1, (n, o) => {
  console.log(JSON.stringify(n), JSON.stringify(o))
  gsap.to(animatedScore1, { duration: 0.5, number: Number(n) || 0 })
})
watch(score2, (n, o) => {
  console.log(JSON.stringify(n), JSON.stringify(o))
  gsap.to(animatedScore2, { duration: 0.5, number: Number(n) || 0 })
})
watch(score3, (n, o) => {
  console.log(JSON.stringify(n), JSON.stringify(o))
  gsap.to(animatedScore3, { duration: 0.5, number: Number(n) || 0 })
})
watch(score4, (n, o) => {
  console.log(JSON.stringify(n), JSON.stringify(o))
  gsap.to(animatedScore4, { duration: 0.5, number: Number(n) || 0 })
})
</script>
<template>
  <div class="fill">
    <Transition name="bounce">
      <QuestionViewer
        v-if="dialogVisible"
        @close="dialogVisible = false"
        :question="neighbours[index]"
        :teams="teams"
        @updateScore="handleUpdateScore"
      />
    </Transition>
    <div class="main-container my-grid fill">
      <div class="map-container fill base-flex">
        <RFMap />
      </div>
      <div class="score-container">
        <div class="score-line">
          <span>{{ teams[0].name }}</span
          >:<span>{{ animatedScore1.number.toFixed(0) }}</span>
        </div>
        <div class="score-line">
          <span>{{ teams[1].name }}</span
          >:<span>{{ animatedScore2.number.toFixed(0) }}</span>
        </div>
        <div class="score-line">
          <span>{{ teams[2].name }}</span
          >:<span>{{ animatedScore3.number.toFixed(0) }}</span>
        </div>
        <div class="score-line">
          <span>{{ teams[3].name }}</span
          >:<span>{{ animatedScore4.number.toFixed(0) }}</span>
        </div>
      </div>
      <div class="controls-container">
        <button class="my-button start-button" @click="dialogVisible = true">?</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.main-container {
  /* background: rgba(99, 35, 35, 0.493); */
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
  grid-row: 1/3;
}

.score-container {
  grid-column: 2;
  grid-row: 1;
}

.controls-container {
  grid-column: 2;
  grid-row: 2;
}

.start-button {
  border-radius: 50%;
  height: 120px;
  font-size: 5rem;
}
</style>
