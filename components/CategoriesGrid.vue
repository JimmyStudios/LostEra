<template>
  <div>
    <div class="CategoriesGrid">
      <a-button type="primary" @click="openModal(category)" v-for="(category, index) in uniqueCategories" :key="index" class="CategoryBlock">
        <p>{{ category }}</p>
      </a-button>
    </div>
    <a-modal v-model:open="modalShow" width="600px" :title="selectedCategory ? selectedCategory.name : ''" @ok="closeModal">
      <div v-if="selectedCategory">
        <div v-for="(pkg, index) in selectedCategory.packages" :key="index">
          <p>
            <span>Name: {{ pkg.name }}</span>
            <span>Base Price: {{ pkg.base_price }}</span>
          </p>
        </div>
      </div>
    </a-modal>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue';

export default defineComponent({
  name: 'CategoriesGrid',
  setup() {
    const packages = ref<any[]>([]);
    const modalShow = ref(false);
    const selectedCategory = ref<any>(null);

    const fetchData = async () => {
      try {
        const response = await fetch('https://headless.tebex.io/api/accounts/ts3t-f21ba89d9d470d6c26371c70e2e5a66f8912e75f/packages', {
          headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
          }
        });
        const responseData = await response.json();
        packages.value = responseData.data;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    };

    const uniqueCategories = computed(() => {
      return [...new Set(packages.value.map(item => item.category.name))];
    });

    const openModal = (category: any) => {
      selectedCategory.value = {
        name: category,
        packages: packages.value.filter(pkg => pkg.category.name === category)
      };
      modalShow.value = true;
    };

    const closeModal = () => {
      modalShow.value = false;
    };

    return {
      packages,
      modalShow,
      selectedCategory,
      fetchData,
      uniqueCategories,
      openModal,
      closeModal
    };
  },
  mounted() {
    this.fetchData();
  }
});
</script>

<style scoped>
.CategoriesGrid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 30px;
  width: 300px;
  margin: 0 auto;
}
.CategoryBlock {
  margin: 0 auto;
  cursor: pointer;
}
</style>
