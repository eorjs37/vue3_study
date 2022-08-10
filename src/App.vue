<template>
  <div class="conatainer">
    <div class="title">
      <h1>Slot</h1>
    </div>

    <ChildComponent :paraentList="testData">
      <template #thead>
        <th>출장비 내역</th>
        <th>출장비 내역</th>
        <th>금액</th>
      </template>

      <template #list="{ row }">
        <td @click="app.click(row)">{{ row.item }}</td>
        <td>{{ row.item2 }}</td>
        <td>{{ row.item3 }}</td>
      </template>
    </ChildComponent>

    <h1>아코디언</h1>

    <input type="checkbox" name="accordion" id="answer1" />
    <label for="answer1">
      새우깡과 매운 새우깡의 차이가 나는 이유는 매운 맛 때문인가요?
      <i class="fas fa-angle-down"></i>
    </label>
    <div>
      <p>새우깡과 매운 새우깡의 차이가 나는 이유는 매운 맛 때문인가요?</p>
    </div>

    <input type="checkbox" name="accordion" id="answer2" />
    <label for="answer2">
      새우깡과 매운 새우깡의 차이가 나는 이유는 매운 맛 때문인가요?
      <i class="fas fa-angle-down"></i>
    </label>
    <div>
      <p>새우깡과 매운 새우깡의 차이가 나는 이유는 매운 맛 때문인가요?</p>
    </div>
  </div>
</template>

<script>
import { reactive, ref } from "vue";
import ChildComponent from "./components/ChileComponent.vue";
export default {
  name: "App",
  components: {
    ChildComponent,
  },
  setup() {
    const testData = ref([
      { item: 1, item2: 2, item3: 3 },
      { item: 1, item2: 2, item3: 3 },
      { item: 1, item2: 2, item3: 3 },
    ]);

    const app = reactive({
      click: (item) => {
        alert(`Click : ${item.item}`);
      },
    });

    return {
      testData,
      app,
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
.conatainer {
  max-width: 1920px;
  width: 100%;
  margin: 0 auto;
  text-align: center;
}

input[id*="answer"] {
  display: none;
}

input[id*="answer"] + label {
  font-size: 1.5em;
  display: flex;
  line-height: 4em;
  justify-content: space-between;
  position: relative;
  border-bottom: 1px solid #d5d5d5;
  cursor: pointer;
}

input[id*="answer"] + label i {
  position: absolute;
  top: 50%;
  right: 0;
  transform: translateY(-50%);
  transition: all 0.3s;
}

input[id*="answer"] + label + div {
  overflow: hidden;
  height: 0;
  display: flex;
  align-items: center;
  transition: all 0.3s;
}

input[id*="answer"] + label + div p {
  display: inline-block;
  padding: 20px 0;
}

input[id*="answer"]:checked + label + div {
  height: 50px;
  border-bottom: 2px solid #d5d5d5;
}

input[id*="answer"]:checked + label i {
  transform: rotate(180deg);
}
</style>
