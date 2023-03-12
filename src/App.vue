<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import RadioButtonField from './components/RadioButtonField.vue';
import ToDoTable from './components/ToDoTable.vue';
</script>

<template>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
              <HelloWorld msg="You did it!" />
                      </div>
                    </header>

                    <main>
                      <TheWelcome />
                    </main> -->

  <!-- 絞り込みラジオボタン -->
  <RadioButtonField v-model="current" v-bind:options="options" name="StateFilterRadio"></RadioButtonField>
  <!-- ToDo テーブル -->
  <ToDoTable v-bind:current="current"></ToDoTable>
</template>

<script>
export default {
  data() {
    return {
      // 状態での絞り込みの選択肢
      options: [
        { value: -1, label: "すべて" },
        { value: 0, label: "作業中" },
        { value: 1, label: "完了" }
      ],
      // 選択している options の value を記憶するためのデータ
      // 初期値を「-1」つまり「すべて」にする
      current: -1,
    };
  },
  components: { RadioButtonField, ToDoTable }
}
</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
