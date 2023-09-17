<template> 
    <v-dialog 
        v-model="dialogAddUserAdmin" 
        max-width="900"  
        scrollable 
        persistent
    >
      <v-card>
        <v-card-title class="headline bg-mea-light color-mea" >Add User Admin</v-card-title>
        <v-card-text>
          <v-form @submit.prevent="registerUser">
            <v-row>
              <v-col>
                <v-combobox
                  label="Combobox"
                  :items="['California', 'Colorado', 'Florida', 'Georgia', 'Texas', 'Wyoming']"
                ></v-combobox>
              </v-col>
            </v-row>
        </v-form>
        </v-card-text>
        <v-card-actions class="bg-mea-light">     
          <v-spacer></v-spacer>
          <v-btn variant="flat" class="color-mea" @click="registerUser">Add</v-btn>
          <v-btn variant="flat" class="color-mea" @click="closeDialog">Cancel</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </template>
  <script>

  export default {
    name: 'dialogAddUserAdmin',
    data() {
      return {
        dialogAddUserAdmin: false,
      };
    },    
    props: {
        msg: String
    },
    methods: {
      openDialog() {
        this.dialogAddUserAdmin = true;
      },
      closeDialog() {
        this.dialogAddUserAdmin = false;
      },
      registerUser() {
        // Implement your user registration logic here
        console.log('Registering user with the following details:');
        // Close the dialog after registration
        this.closeDialog();
      },
    },
  };
  </script>
  