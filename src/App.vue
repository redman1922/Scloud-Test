<script setup>
import Header from '@/components/Header/Header.vue'
import DragAndDrop from '@/components/DragAndDrop/DragAndDrop.vue'
import { computed, onMounted, provide, ref, watch } from 'vue'

let id = ref(0)

const cardList = [
  {
    id: id.value++,
    text: 'Сварить пельмени',
    status: 'Открыт'
  },
  {
    id: id.value++,
    text: 'Поднять инфрастуктуру проекта',
    status: 'Открыт'
  },
  {
    id: id.value++,
    text: 'Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу',
    status: 'В работе'
  },
  {
    id: id.value++,
    text: 'Поругаться с девопсом',
    status: 'В работе'
  },
  {
    id: id.value++,
    text: 'Спеть - Знаешь ли ты, вдоль ночных дорог',
    status: 'Закрыт'
  }
]

const cards = ref([])

const statusCountsAndCards = computed(() => cards.value.reduce((accumulator, card) => {
    accumulator.counts[card.status] = (accumulator.counts[card.status] || 0) + 1

    accumulator.cards[card.status].push(card)

    return accumulator
  }, {
    counts: {},
    cards: {
      'Открыт': [],
      'В работе': [],
      'Закрыт': []
    }
  })
)

onMounted(() => {
  const currentCards = localStorage.getItem('cards')
  if (currentCards) {
    cards.value = JSON.parse(currentCards)
  } else {
    cards.value = [...cardList]
    localStorage.setItem('cards', JSON.stringify(cardList))
  }
})

const addToCards = (item) => {
  cards.value.push(item)
}

const updateCards = ({ id, text, status }) => {
  const index = cards.value.findIndex(card => card.id === id)
  if (index !== -1) {
      cards.value[index].text = text
      cards.value[index].status = status
  } else {
    console.error('Карточка с указанным ID не найдена')
  }
}

const removeCards = (id) => {
  const index = cards.value.findIndex(card => card.id === id)
  if (index !== -1) {
    cards.value.splice(index, 1)
  } else {
    console.error('Карточка с указанным ID не найдена')
  }
}

const changeCardStatus = (id, status) => {
  const index = cards.value.findIndex(card => card.id === id)
  if (index !== -1) {
    cards.value[index].status = status
  } else {
    console.error('Карточка с указанным ID не найдена')
  }
}

watch(
  cards,
  () => {
    localStorage.setItem('cards', JSON.stringify(cards.value))
  },
  { deep: true }
)
provide('cards', {
  cards,
  addToCards,
  statusCountsAndCards,
  id,
  updateCards,
  removeCards,
  changeCardStatus
})

</script>

<template>
  <header class="wrapper-changing-tasks">
    <Header />
  </header>
  <main class="wrapper-view-tasks">
    <DragAndDrop />
  </main>
  <footer class="footer"></footer>
</template>

<style lang="scss" scoped>
@import './common/varibles';
@import './common/mixins';

.wrapper-changing-tasks {
  background-color: $color-gray;
  padding: 64px 0;
}

.wrapper-view-tasks {
  width: 100%;
  max-width: 1200px;
  margin: 60px auto 0;
  padding-bottom: 208px;
}

.footer {
  background: $color-dark-gray;
  height: 148px;
  border-radius: 48px 48px 0 0;
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
}

@media screen and (max-width: 1190px) {
  .wrapper-changing-tasks {
    padding: 64px 1%;
  }

  .wrapper-view-tasks {
    padding: 0 1% 208px;
  }
}

@media screen and (max-width: $tablet) {
  .wrapper-changing-tasks {
    padding: 48px 4% 180px;
  }

  .wrapper-view-tasks {
    display: none;
  }
  .footer {
    height: 120px;
  }
}

@media screen and (max-width: $phone) {
  .wrapper-changing-tasks {
    padding: 32px 4% 140px;
  }
  .footer {
    height: 80px;
  }
}
</style>
