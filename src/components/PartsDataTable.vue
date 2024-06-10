<!-- PartsDataTable.vue -->
<template>
    <div>
      <h2>Parts</h2>
      <DataTable v-if="products.length"
        :value="products"
        lazy
        size="small"
        paginator
        selection-mode="single"
        data-key="id"
        :rows="5"
        :first="first"
        :total-records="totalRecords"
        :rows-per-page-options="[5, 10, 20, 50]" @page="onPage($event)" >
        <Column field="type" header="Type"></Column>  
        <Column field="shortCode" header="Short Code"></Column>
        <Column field="name" header="Name"></Column>
        <Column field="createdAt" header="Created At"></Column>
        <!-- <Column field="image" header="Image">
            <template #body="slotProps">
                <img :src="slotProps.data.image" alt="Product Image" style="max-width: 100px; max-height: 100px;">
            </template>
        </Column> -->
      </DataTable>
    </div>
   
  </template>
  
  <script>
  import { ref, onMounted } from 'vue';
  import DataTable from 'primevue/datatable';
  import Column from 'primevue/column';
  import axios from 'axios';
  
  export default {
    name: 'PartsDataTable',
    components: {
      DataTable,
      Column
    },
    setup() {
      const products = ref([]);
      const totalRecords = ref(0);
      const first = ref(0);
      const tableParams = ref({
        page: 0,
        first: 0,
        rows: 5,
        pageCount: 0,
      })
      const getParts= async() => {
        console.log('Page changed:', tableParams.value.page);
        console.log('Number of rows:', tableParams.value.rows);
        const response = await axios.get(`http://localhost:8000/api/v1/parts?search=string&page=${tableParams.value.page+1}&size=${tableParams.value.rows}`);
        products.value = response.data.items;       
        totalRecords.value=response.data.total
      }
      onMounted(async () => {
        getParts()

      });
      const onPage = async(event) => {
        tableParams.value = {
          ...tableParams.value,
          page:event.page,
          rows:event.rows
        }
    
      getParts()
      // const response = await axios.get(`http://localhost:8000/api/v1/parts?search=string&page=${event.page+1}&size=${event.rows}`);
      // products.value = response.data.items;       
    // totalRecords.value=response.data.items.length
      // Fetch new data based on the new page index and number of rows per page
      // For example, fetchData(event.page, event.rows);
    };

  
      return {
        products,
        first,
        totalRecords,
        onPage
      };
    }
  };
  </script>
  
  <style scoped>
  h2 {
    margin-bottom: 1rem;
  }
  </style>
  