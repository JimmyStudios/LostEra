<template>

<div>

<div class="CategoriesGrid">

<div class="CategoryBlock">
  <a-button class="ModalBTN" type="primary" @click="showModal">Category 1</a-button>
</div>
<div class="CategoryBlock">
  <a-button class="ModalBTN" type="primary" @click="showModal">Category 2</a-button>
</div>
<div class="CategoryBlock">
  <a-button class="ModalBTN" type="primary" @click="showModal">Category 3</a-button>
</div>
<div class="CategoryBlock">
  <a-button class="ModalBTN" type="primary" @click="showModal">Category 4</a-button>
</div>
<div class="CategoryBlock">
  <a-button class="ModalBTN" type="primary" @click="showModal">Category 5</a-button>
</div>
<div class="CategoryBlock">
  <a-button class="ModalBTN" type="primary" @click="showModal">Category 6</a-button>
</div>


</div>

<a-modal v-model:open="open" width="1000px" title="Category Name" @ok="handleOk">
<p>Some contents...</p>
<p>Some contents...</p>
<p>Some contents...</p>
</a-modal>

</div>

</template>

<style scoped>



.CategoriesGrid {
    display: grid;
    grid-template-columns: repeat(3,1fr);
    grid-gap: 30px;
    width: 300px;
    margin: 0px auto;
}
.ModalBTN {
  margin: 0px auto;
  width: fit-content;
  position: relative;
    display: block;
}


</style>

<script lang="ts" setup>
import { ref } from 'vue';
const open = ref<boolean>(false);

const showModal = () => {
  open.value = true;
};

const handleOk = (e: MouseEvent) => {
  console.log(e);
  open.value = false;
};
</script>