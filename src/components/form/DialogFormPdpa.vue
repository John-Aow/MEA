<template> 
    <v-dialog 
        v-model="dialogFormPdpa" 
        max-width="900"  
        scrollable 
        persistent
    >
      <v-card>
        <v-card-title class="headline bg-mea-light color-mea" >PDPA</v-card-title>
        <v-card-text>
          <div>
            <h3>The standard Lorem Ipsum passage, used since the 1500s</h3>
"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
          </div>
          <div>
            <h3>The standard Lorem Ipsum passage, used since the 1500s</h3>
"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
          </div>
          <div>
            <h3>The standard Lorem Ipsum passage, used since the 1500s</h3>
"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
          </div>
          <div>
            <h3>The standard Lorem Ipsum passage, used since the 1500s</h3>
"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
          </div>
          <div>
            <h3>The standard Lorem Ipsum passage, used since the 1500s</h3>
"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
          </div>
        </v-card-text>
        <v-card-actions class="bg-mea-light">     
            <v-checkbox v-model="checkbox">
            <template v-slot:label>
              <div>
                accept   
              </div>
            </template>
          </v-checkbox>
          <v-spacer></v-spacer>
          <v-btn variant="flat" class="color-mea" @click="closeDialog">Cancel</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </template>
  
  <script>
  export default {
    name: 'FormPdpa',

    data() {
      return {
        dialogFormPdpa: false,    
      };
    },    
  
    methods: {  
      openDialog() {
        this.dialogFormPdpa = true;
      },
      closeDialog() {
        this.dialogFormPdpa = false;
      },
   
    },
  };
  </script>
  