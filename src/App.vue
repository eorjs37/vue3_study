<template>
  <div class="conatainer">
    <div class="title">
      <h1>
        Slot
      </h1>
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
  </div>
</template>

<script>
import { reactive, ref, onMounted } from 'vue';
import ChildComponent from '@/components/ChileComponent.vue';
export default {
  name: 'App',
  components:{
    ChildComponent
  },
  setup(){
    const testData = ref(
      [
        { item:1, item2:2,item3:3},
        { item:1, item2:2,item3:3},
        { item:1, item2:2,item3:3},
      ]
    )

    const app = reactive(
      {
        click: (item)=>{
          alert(`Click : ${item.item}`)
        }
      }
    )

    onMounted(()=>{
      console.log('App onMounted');
    });
    
    return{
      testData,
      app
    }
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
.conatainer{
  max-width: 1920px;
  width: 100%;
  margin: 0 auto;
  text-align: center;
  background-color: #eee;
}
</style>
