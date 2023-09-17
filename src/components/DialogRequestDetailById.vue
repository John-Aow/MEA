<template> 
    <v-dialog 
        v-model="dialogRequestDetailById" 
        max-width="1100"  
        scrollable 
        persistent
    >
      <v-card>
        <v-card-title class="headline bg-mea-light color-mea" >{{ msg }}</v-card-title>
        <v-card-text>
          <v-row no-gutters>
            <v-col cols="6">
              Request ID : 202307001
            </v-col>
            <v-col cols="6">
              Project Name :  Test
            </v-col>
            
          </v-row>
          <v-row no-gutters>  
            <v-col cols="6">
              Requester :  Panumas Panyacharoenchai
            </v-col>
            <v-col cols="6">
              Department :  Test
            </v-col>
          </v-row>
          <v-row no-gutters>
            <v-col cols="6">
              Document Date :  23/07/2023
            </v-col>
          
            <v-col cols="6">
              Detail : ..........................
            </v-col>
          </v-row>
          <v-divider class="mt-3"></v-divider>

          <v-card class="mx-auto mb-2" > 
          <v-row class="pa-4">
              <v-col
                  v-for="n in 5"
                  :key="n"
                  cols="3"
                  sm="3"   
              >
                <CardVmDetail page="detail"></CardVmDetail>
          </v-col>
          </v-row>
          </v-card>

          <v-card
            :loading="loading"
            class="mx-auto"
          >
            <v-card-title class="color-mea">Flow Approval</v-card-title>
            <v-card-text> 
              <TableFlowApproveDetail class="mt-2" />
              <FormApprove  />
            </v-card-text>
          </v-card>
          <FormAdminAnlysis></FormAdminAnlysis>
          </v-card-text>
        <v-card-actions class="bg-mea-light">     
          <v-spacer></v-spacer>
          <v-btn variant="flat" class="color-mea" @click="closeDialog">Cancel</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </template>
  
  <script>
  import FormApprove from '@/components/form/FormApprove.vue'
  import CardVmDetail from '@/components/CardVmDetail.vue'
  import TableFlowApproveDetail from '@/components/TableFlowApproveDetail.vue'
  import FormAdminAnlysis from '@/components/form/FormAdminAnlysis.vue'

  export default {
    name: 'RequestDetailById',
    components: {
      FormApprove,
      CardVmDetail,
      TableFlowApproveDetail,
      FormAdminAnlysis
    },
    data() {
      return {
        dialogRequestDetailById: false,
        loading:false,
        host_name: '',
        os: '',
        zone: '',
        cpu_count: 2,
        disk: 100,
      };
    },    
    props: {
        msg: String,
    },
    methods: {
      openDialog() {
        this.dialogRequestDetailById = true;
      },
      closeDialog() {
        this.dialogRequestDetailById = false;
      },
   
    },
  };
  </script>
  