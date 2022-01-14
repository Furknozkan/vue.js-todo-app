<template>
<div class="my-2">
      <input type="text" placeholder="Bir görev gir..." @keydown.enter="onSave" />
    </div>
</template>

<script>
export default {
    inject : ["onSave"]
}
</script>