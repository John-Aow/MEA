<template>
  <v-container>
    <h2 class="my-3 color-mea">Manage Admin</h2>
    <TableAdminDetail></TableAdminDetail>
  </v-container>
   
</template>
    
    <script>
    // @ is an alias to /src
    import TableAdminDetail from '@/components/TableAdminDetail.vue'

    export default {
      name: 'Manage-Admin-Page',
      components: {
        TableAdminDetail,
      }
    }
</script>
    