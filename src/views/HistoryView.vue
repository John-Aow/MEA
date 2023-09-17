<template>
  <div class="home"> 
    <v-container fluid>     
      <v-card class="mx-auto">   
        <v-tabs
          v-model="tab"
          class="color-mea"
          align-tabs="center"
        >
        <v-tab value="1" width="50%">Request VM All Status</v-tab>
        <v-tab value="2" width="50%"><v-badge :content="5"  color="error">Waiting Approval </v-badge></v-tab>
         
        </v-tabs>
        <v-window v-model="tab">

          <v-window-item value="1" >
          <v-card>
            <v-card-text>

            <FilterHeaderHome /> 
            <TableRequestVmDetail />
            <DialogFormPdpa ref="DialogFormPdpa" />
            
            </v-card-text>
          </v-card>
          </v-window-item>

          <v-window-item value="2" >
          <v-card>
            <v-card-text>
            <TableRequestVmDetail />
            </v-card-text>
          </v-card>
          </v-window-item>
          
        </v-window>
      </v-card>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src

import FilterHeaderHome from '@/components/FilterHeaderHome.vue'
import TableRequestVmDetail from '@/components/TableRequestVmDetail.vue'
import DialogFormPdpa from '@/components/form/DialogFormPdpa.vue'

export default {
  name: 'HomeView',
  components: {
    FilterHeaderHome,
    TableRequestVmDetail,
    DialogFormPdpa
  },
  data() {
    return {  
      tab: null,
    };
  },
  methods: {
    openDialogPdpa(){
      this.$refs.DialogFormPdpa.openDialog;
    }
  },
  mounted(){
    //this.openDialogPdpa(); 
  }
 
}
</script>
