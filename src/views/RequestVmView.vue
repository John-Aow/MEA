<template>
    <v-container>
        <div class="text-h5 text-center">Request VM</div>
        <div class="text-h6 text-left">Personal Information</div>
        <v-divider class="my-2"></v-divider>
        <v-row>
            <v-col cols="4">
                <div class="text-left">Name: Jane Doe</div> 
            </v-col>
            <v-col cols="4">
                <div class="text-left">Department: Test2</div>            
            </v-col>
            <v-col cols="4">
                <div class="text-left">Approver: Manager1 Demo</div>   
            </v-col>
            <v-col cols="4">
                <div class="text-left">Section: Section 1</div> 
            </v-col>
            <v-col cols="4">
                <div class="text-left">Section-Code: TST</div>            
            </v-col>
            <v-col cols="4">
                <v-text-field  label="Telephone"  variant="outlined" clearable required></v-text-field>
            </v-col>
  
        </v-row>

        <div class="text-h6 text-left">Project Information</div>
        <v-divider class="my-2"></v-divider>
        <v-row class="mb-0">
            <v-col cols="2">
                <div class="text-left">Project Name :</div> 
            </v-col>
            <v-col cols="10">
                <v-text-field v-model="projectName" label="Project Name" variant="outlined" clearable required></v-text-field>
            </v-col>

            <v-col cols="2">
                <v-list-subheader>Reason for Request :</v-list-subheader>
            </v-col>
            <v-col cols="10">
                <v-text-field v-model="reasonForRequest" label="Reason for Request"  variant="outlined" clearable  required></v-text-field>
            </v-col>
        </v-row>
        <v-row>
            
        </v-row>
        <v-row>
            <v-col cols="2">
                <v-list-subheader>Active Date :</v-list-subheader>
            </v-col>
            <v-col cols="10">
                <v-text-field v-model="activeDate" label="Active Date"  variant="outlined" clearable  required></v-text-field>
            </v-col>
        </v-row>
        <div class="text-h6 text-left">VM Details</div>
        <v-divider class="my-2"></v-divider>
        <FormAddVm ref="DialogAddVm" :msg=HeaderDialogRequest></FormAddVm>

        <v-row class="pa-4">
            <v-col >
                <v-card 
                    justify="center"
                    @click="openDialogAddVM" 
                    height="100%"
                    class=" d-flex flex-column"
                >
                <v-spacer></v-spacer>
                <v-card-text >
                    <v-row class="text-center"  justify="center">
                        <v-icon icon="mdi-plus" size="large" class="mr-2"></v-icon>
                        <p class="font-weight-medium" >Add VM</p>
                    </v-row>
                    </v-card-text>
                <v-spacer></v-spacer>
                </v-card>
            </v-col>
            <v-col v-for="n in 5" :key="n" cols="3" sm="3">
                <CardVmDetail page="add_vm"></CardVmDetail>
            </v-col>
        </v-row>
        
    <v-row class="my-2 text-center" justify="center">
        <v-btn variant="tonal" class="color-mea ml-2" @click="registerUser">Draft</v-btn>
        <v-btn variant="tonal" class="color-mea ml-2" @click="registerUser">Send to Approve</v-btn>
        <v-btn variant="tonal" class="color-mea ml-2" @click="closeDialog">Cancel</v-btn>
    </v-row>
       
    </v-container>
</template>
    
<script>
import FormAddVm from '@/components/form/DialogFormAddVm.vue'
import CardVmDetail from '@/components/CardVmDetail.vue'
export default {
    name: 'Request-Vm',
    components: {
        CardVmDetail,
        FormAddVm

    },
    data() {
        return {
            projectName: "",
            reasonForRequest: "",
            activeDate: "",
            HeaderDialogRequest: "",
        }
    },
    methods: {
        openDialogAddVM() {
        // Access the dialog component using its reference and call the openDialog method
        this.HeaderDialogRequest = 'Add VM';
        this.$refs.DialogAddVm.openDialog();
      },
      closeDialog() {
        // this.dialogVisible = false;
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

    }
}
</script>
    