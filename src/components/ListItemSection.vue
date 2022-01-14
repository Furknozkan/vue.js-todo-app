<template>
      <ul v-if="provideData.itemsList.length > 0">
      <li v-for="item in provideData.itemsList" :key="item.id" class="d-flex justify-content-between align-items-center">
        <span>{{ item.title }}</span>
        <button @click="onDelete(item)" class="sm red">Sil</button>
      </li>
    </ul>
    <div v-else class="bg-blue text-white">
      Herhangi bir görev yok..
    </div>
</template>

<script>
export default {
        inject: ["provideData", "onDelete"]
}
</script>