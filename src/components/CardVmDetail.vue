<template>
  <v-card :loading="loading" class="mx-auto" max-width="374">
    <template v-slot:loader="{ isActive }">
      <v-progress-linear :active="isActive" color="deep-purple" height="4" indeterminate></v-progress-linear>
    </template>


    <v-card-item>
      <v-card-title>
        <v-icon icon="fa:fa-brands fa-windows " size="small" class="mr-2"></v-icon>
        Test
      </v-card-title>
    </v-card-item>

    <v-card-text>
      <div>CPU Count : 8</div>
      <div>Memmory : 500 GB</div>
      <div>Zone : Production</div>
    </v-card-text>

    <v-divider v-if="page === 'add_vm'" class="mx-4 mb-1"></v-divider>

    <v-card-actions v-if="page === 'add_vm'">

      <v-spacer></v-spacer>
      <v-btn @click="openDialogAddVM" icon="fa:fas fa-edit ">
      </v-btn>
      <v-btn icon="fa:fa-solid fa-trash-can ">
      </v-btn>
      <!-- Use the Form Add Vm component -->
      <FormAddVm ref="DialogAddVm" :msg=HeaderDialogRequest></FormAddVm>
    </v-card-actions>
  </v-card>
</template>
<script>
import FormAddVm from '@/components/form/DialogFormAddVm.vue'
export default {
  name: 'CardVmDetail',
  components: {
    FormAddVm
  },
  props: {
    page: String
  },

  data: () => ({
    HeaderDialogRequest: '',
    loading: false,
    selection: 1,
  }),

  methods: {
    reserve() {
      this.loading = true

      //setTimeout(() => (this.loading = false), 2000)
    },
    openDialogAddVM() {
      // Access the dialog component using its reference and call the openDialog method
      this.HeaderDialogRequest = 'Edit VM';
      this.$refs.DialogAddVm.openDialog();
    },
  },
}
</script>