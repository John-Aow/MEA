<template>
  <v-dialog 
    v-model="dialogFlowDetail" 
    max-width="700"  
  >
    <v-card>
        <v-card-title class="headline bg-mea-light color-mea" >Flow Detail</v-card-title>
        <v-card-text>
            <TableFlowApproveDetail />
        </v-card-text>
    </v-card>
  </v-dialog>
</template>
    
    <script>
    // @ is an alias to /src
  
    import TableFlowApproveDetail from '@/components/TableFlowApproveDetail.vue'
    export default {
      name: 'Header-Page',
      components: {
        TableFlowApproveDetail
      },
      data() {
        return {
          dialogFlowDetail: false,
        }
    },
      methods: {
        openDialog() {
          this.dialogFlowDetail = true;
        },
        closeDialog() {
          this.dialogFlowDetail = false;
        },
   },
    }
    </script>
    