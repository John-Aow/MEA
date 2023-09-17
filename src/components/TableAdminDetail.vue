<template>
    <v-data-table
      v-model:items-per-page="itemsPerPage"
      :headers="headers"
      :items="all_user_admin"
      class="elevation-1"
    >
      <template v-slot:top>
        <v-toolbar flat >
            <v-spacer></v-spacer>
             <!-- Use the component -->
            <DialogFormAdduserAdmin ref="DialogFormAdduserAdmin" />
             <!-- Use the component -->
            <v-btn class="color-mea" @click="openDialogFormAdduserAdmin">Add User Admin</v-btn>
        </v-toolbar>
      </template>

      <template v-slot:item="row">
        <tr>
          <td>{{ row.item.index + 1 }}</td>
          <td>{{ row.item.selectable.username }}</td>
          <td>{{ row.item.selectable.emp_id }}</td>
          <td>{{ row.item.selectable.name }}</td>
          <td>{{ row.item.selectable.email }}</td>
          <td>
            <div>
                <v-chip
                  class="ma-2"
                  label
                  link
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
    <DialogConfirm msg="Confirm Delete User Admin" title="Delete User !!" ref="DialogConfirm"/>
</template>

<script>
    import DialogFormAdduserAdmin from '@/components/form/DialogFormAdduserAdmin.vue'
    import DialogConfirm from '@/components/DialogConfirm.vue'

    export default {
        components: {
            DialogFormAdduserAdmin,
            DialogConfirm
        },
        data () {
          return {
            HeaderDialogRequest: '',
            HeaderDialogRequestDetailById: '',
            itemsPerPage: 5,
            headers: [
                { title: 'No', key: 'no', },
                { title: 'Username', key: 'username', },
                { title: 'Employee ID', key: 'emp_id' , },
                { title: 'Name', key: 'name' , },
                { title: 'Email', key: 'email' , },
                { title: 'Action', key: 'action' , sortable: false},
            ],
          all_user_admin: [
            { 
              username: 'panumaspa',
              emp_id: '9000931',
              name: 'Panumas Panyacharoen',
              email: 'panumaspa@yipintsoi.com',
            },
            {
              username: 'panumaspa',
              emp_id: '9000931',
              name: 'Panumas Panyacharoen',
              email: 'panumaspa@yipintsoi.com',
            },
            {
              username: 'panumaspa',
              emp_id: '9000931',
              name: 'Panumas Panyacharoen',
              email: 'panumaspa@yipintsoi.com',
            }, 
          ],
          }
        },
        methods: {
        openDialogFormAdduserAdmin() {
          // Access the dialog component using its reference and call the openDialog method
          this.$refs.DialogFormAdduserAdmin.openDialog();
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