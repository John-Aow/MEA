<template>
    <v-data-table
      v-model:items-per-page="itemsPerPage"
      :headers="headers"
      :items="desserts"
      class="elevation-1"
    >
      <template v-slot:top>
        <v-toolbar flat >
            <v-toolbar-title class="color-mea text-left">Request VM All Status</v-toolbar-title>
            <v-divider
              class="mx-2"
              inset
              vertical
            ></v-divider>
            <v-spacer></v-spacer>
             <!-- Use the component -->
            <DialogFormRequestVm ref="DialogFormRequestVm" :msg=HeaderDialogRequest ></DialogFormRequestVm>
            <DialogRequestDetailById ref="RequestDetailById" :msg=HeaderDialogRequestDetailById ></DialogRequestDetailById>
            
             <!-- Use the component -->
            <v-btn class="color-mea" >Create Request Database</v-btn>
            <v-btn class="color-mea" @click="openDialogRequestVM">Create Request VM</v-btn>
        </v-toolbar>
      </template>

      <template v-slot:item="row">
        <tr>
          <td>{{ row.item.index + 1 }}</td>
          <td>{{ row.item.selectable.request_id }}</td>
          <td>{{ row.item.selectable.project_name }}</td>
          <td>{{ row.item.selectable.requester }}</td>
          <td>{{ row.item.selectable.department }}</td>
          <td>{{ row.item.selectable.doc_date }}</td>
          <td>{{ row.item.selectable.doc_type }}</td>
          <td>
            <div>
                <v-chip
                  class="ma-2"
                  v-if="row.item.selectable.status === 'Reject'"
                >
                {{ row.item.selectable.status }}
                </v-chip>
              
                <v-chip
                  class="ma-2"
                  color="primary"   
                  v-if="row.item.selectable.status === 'Waiting Approve'"
                  @click="OpenDialogFlow"
                >
                  {{ row.item.selectable.status }}
                </v-chip>

                <v-chip
                  class="ma-2"
                  color="teal"
                  v-if="row.item.selectable.status === 'Approve'"
                  @click="OpenDialogFlow"
                >
                  {{ row.item.selectable.status }}
                </v-chip>
              
                <v-chip
                  class="ma-2"
                  color="orange"
                  v-if="row.item.selectable.status === 'Draft'"
                >
                  {{ row.item.selectable.status }}
                </v-chip>
              
                <v-chip
                  class="ma-2"
                  color="red"
                  text-color="white"
                  v-if="row.item.selectable.status === 'Not complete'"
                >
                  {{ row.item.selectable.status }}
                </v-chip>
              
                <v-chip
                  class="ma-2"
                  color="green"
                  text-color="white"
                  v-if="row.item.selectable.status === 'Complete'"
                  @click="OpenDialogFlow"
                >
                  {{ row.item.selectable.status }}
                </v-chip>
            </div>
          </td>
          <td>
            <div>
                <v-chip
                  class="ma-2"
                  link
                  label
                  @click="openDialogRequestDetailById"
                  v-if="row.item.selectable.status === 'Waiting Approve'"
                >
                  <v-icon start icon="mdi-eye"></v-icon>
                  Approval
                </v-chip>

                <v-chip
                  class="ma-2"
                  link
                  label
                  @click="openDialogRequestDetailById"
                  v-if="row.item.selectable.status !== 'Waiting Approve'"
                >
                  <v-icon start icon="mdi-eye"></v-icon>
                  View
                </v-chip>

                <v-chip
                  class="ma-2"
                  link
                  label
                  text-color="white"
                  v-if="row.item.selectable.status === 'Draft' || row.item.selectable.status === 'Waiting Approve'"
                  @click="openDialogRequestVM"
                >
                
                  <v-icon start icon="mdi-pencil" ></v-icon>
                  Edit
                </v-chip>

                <v-chip
                  class="ma-2"
                  label
                  link
                  v-if="row.item.selectable.status === 'Draft'"
                  @click="OpenDialogConfirm"
                >
                  <v-icon start icon="mdi-delete"></v-icon>
                  Delete
                </v-chip>

                
            </div>  
          </td>
        </tr>
      </template>
    </v-data-table>
    <v-btn type="submit" block class="my-3 color-mea">Export to Excel</v-btn>
    <DialogFlowDetail ref="DialogFlowDetail"/>
    <DialogConfirm msg="Confirm Delete Item" title="Delete ITem !!" ref="DialogConfirm"/>
</template>

<script>
    import DialogFormRequestVm from '@/components/form/DialogFormRequestVm.vue'
    import DialogRequestDetailById from '@/components/DialogRequestDetailById.vue'
    import DialogFlowDetail from '@/components/DialogFlowDetail.vue'
    import DialogConfirm from '@/components/DialogConfirm.vue'

    export default {
        components: {
            DialogFormRequestVm,
            DialogRequestDetailById,
            DialogFlowDetail,
            DialogConfirm
        },
        data () {
          return {
            HeaderDialogRequest: '',
            HeaderDialogRequestDetailById: '',
            itemsPerPage: 5,
            headers: [
                { title: 'No', key: 'no' , sortable: false,  },
                { title: 'Request ID', key: 'request_id', },
                { title: 'Project', key: 'project_name' , },
                { title: 'Requester', key: 'requester' , },
                { title: 'Department', key: 'department' , },
                { title: 'Document Date', key: 'doc_date' , },
                { title: 'Document Type', key: 'doc_type' , },
                { title: 'Status', key: 'status'},
                { title: 'Action', key: 'action' , sortable: false},
            ],
          desserts: [
            { 
              request_id: '202307001',
              project_name: 'Test',
              department: 'IT',
              doc_date: '23/07/2023',
              doc_type: 'Database',
              requester: 'Panumas',
              status: 'Complete',
            },
            {
              
              request_id: '202307002',
              project_name: 'Test',
              department: 'IT',
              doc_date: '23/07/2023',
              doc_type: 'VM',
              requester: 'Panumas',
              status: 'Not complete',
            },
            {
              
              request_id: '202307003',
              project_name: 'Test',
              department: 'IT',
              doc_date: '23/07/2023',
              doc_type: 'Database',
              requester: 'Panumas',
              status: 'Draft',
            },
            {
              
              request_id: '202307004',
              project_name: 'Test',
              department: 'IT',
              doc_date: '23/07/2023',
              doc_type: 'VM',
              requester: 'Panumas',
              status: 'Approve',
            },
            {
             
              request_id: '202307005',
              project_name: 'Test',
              department: 'IT',
              doc_date: '23/07/2023',
              doc_type: 'VM',
              requester: 'Panumas',
              status: 'Reject',
            },
            {
             
              request_id: 'Frozen Yogurt',
              project_name: 159,
              department: 6.0,
              doc_date: 24,
              status: 'Waiting Approve',
              requester: 'Panumas',
              doc_type: 'VM',
            },
            {
              
              request_id: 'Frozen Yogurt',
              project_name: 159,
              department: 6.0,
              doc_date: 24,
              status: 'Approve',
              requester: 'Panumas',
              doc_type: 'VM',
            },
   
          ],
          }
        },
        methods: {
        openDialogRequestVM() {
          // Access the dialog component using its reference and call the openDialog method
          this.HeaderDialogRequest = 'Create Request VM';
          this.$refs.DialogFormRequestVm.openDialog();
        },
        openDialogRequestDetailById() {
          this.HeaderDialogRequestDetailById = 'Request VM Detail';
          this.$refs.RequestDetailById.openDialog();
        },
        OpenDialogFlow() {   
          this.$refs.DialogFlowDetail.openDialog();
        },
        OpenDialogConfirm() {   
          this.$refs.DialogConfirm.openDialog();
        },
        
    },
    
    mounted(){
      if(this.$route.meta.isOpenDialog === true){
        this.openDialogRequestDetailById();
      }  
    }
}
</script>