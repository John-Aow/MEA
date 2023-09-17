<template> 
    <v-dialog 
        v-model="dialogVisible" 
        max-width="1100"  
        scrollable 
        persistent
    >
      <v-card>
        <v-card-title class="headline color-mea">{{ msg }}</v-card-title>
        <v-divider></v-divider>
        <v-card-text>
          <v-form @submit.prevent="registerUser">
            <v-row>
              <v-col cols="6" >
                <v-text-field v-model="username" label="Project Name" required></v-text-field>
              </v-col>
              <v-col cols="6" >
                <v-select
                  v-model="user_approval" 
                  label="Approval Name"
                  :items="['California', 'Colorado', 'Florida', 'Georgia', 'Texas', 'Wyoming']"
                  required
                  ></v-select>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12" >
                <v-text-field v-model="password" label="Detail" required type="password"></v-text-field>
              </v-col>
            </v-row>

            <!-- Use the Form Add Vm component -->
            <FormAddVm ref="DialogAddVm" :msg=HeaderDialogRequest ></FormAddVm>
            <v-btn block variant="tonal" class="color-mea" @click="openDialogAddVM">Add VM</v-btn>
            
            <v-card class="mx-auto mt-4">
                <v-row class="pa-4">
                    <v-col
                        v-for="n in 5"
                        :key="n"
                        cols="3"
                        sm="3"   
                    >
                      <CardVmDetail page="add_vm"></CardVmDetail>
                </v-col>
                </v-row>
            </v-card>
        </v-form>
        </v-card-text>
        <v-divider></v-divider>
        <v-card-actions>
          <v-checkbox v-model="checkbox">
            <template v-slot:label>
              <div>
                I agree that
                <v-tooltip location="bottom">
                  <template v-slot:activator="{ props }">
                    <a
                      target="_blank"
                      href="https://vuetifyjs.com"
                      v-bind="props"
                      @click.stop
                    >
                      more
                    </a>
                  </template>
                  Opens in new window
                </v-tooltip>
              </div>
            </template>
          </v-checkbox>
          <v-spacer></v-spacer>
          <v-btn variant="tonal" class="color-mea" @click="registerUser">Draft</v-btn>
          <v-btn variant="tonal" class="color-mea" @click="registerUser">Send to Approve</v-btn>
          <v-btn variant="tonal" class="color-mea" @click="closeDialog">Cancel</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    
  </template>
  
  <script>
  import FormAddVm from '@/components/form/DialogFormAddVm.vue'
  import CardVmDetail from '@/components/CardVmDetail.vue'
  export default {
    name: 'RequestVMForm',
    components: {
        CardVmDetail,
        FormAddVm
    },
    data() {
      return {
        HeaderDialogRequest: '',
        dialogVisible: false,
        username: '',
        email: '',
        password: '',
        user_approval:'',
      };
    },
    
    props: {
        msg: String
    },
    methods: {
      openDialog() {
        this.dialogVisible = true;
      },
      closeDialog() {
        this.dialogVisible = false;
      },
      registerUser() {
        // Implement your user registration logic here
        console.log('Registering user with the following details:');
        console.log('Username:', this.username);
        console.log('Email:', this.email);
        console.log('Password:', this.password);
  
        // Close the dialog after registration
        this.closeDialog();
      },
      openDialogAddVM() {
      // Access the dialog component using its reference and call the openDialog method
      this.HeaderDialogRequest = 'Add VM';
      this.$refs.DialogAddVm.openDialog();
      },
    },
  };
  </script>
