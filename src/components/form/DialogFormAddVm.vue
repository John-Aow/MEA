<template> 
    <v-dialog 
        v-model="dialogAddVm" 
        max-width="900"  
        scrollable 
        persistent
    >
      <v-card>
        <v-card-title class="headline bg-mea-light color-mea" >{{ msg }}</v-card-title>
        <v-card-text>
          <v-form @submit.prevent="btnAddVm">
            <v-row>
              <v-col cols="4" >
                <v-text-field v-model="host_name" label="Host Name" required></v-text-field>
              </v-col>
              <v-col cols="4" >
                <v-select
                  v-model="os" 
                  label="OS"
                  :items="['Windows', 'Ubantu', 'CentOS', 'Redhat', ]"
                  required
                  >
                </v-select>
              </v-col>
              <v-col cols="4" >
                <v-text-field 
                  v-model="memmory" 
                  label="Memmory" 
                  prefix="MB"
                  required
                >
                <template v-slot:append-inner>
                  <v-icon
                  @click="plusMemmory"
                    icon="mdi-plus"
                  />
                  <v-icon
                  @click="minusMemmory"
                    icon="mdi-minus"
                  />
                </template>
              </v-text-field>
              </v-col>
            </v-row>
          
            <v-row>
              <v-col cols="4" >
                <v-text-field 
                  v-model="disk" 
                  label="Disk" 
                  required
                >
                <template v-slot:append-inner>
                  <v-icon
                  @click="plusDisk"
                    icon="mdi-plus"
                  />
                  <v-icon
                  @click="minusDisk"
                    icon="mdi-minus"
                  />
                </template>
              </v-text-field>
              </v-col>
              <v-col cols="4" >
                <v-text-field 
                  v-model="cpu_count" 
                  label="CPU Count" 
                  required
                >
                <template v-slot:append-inner>
                  <v-icon
                  @click="plusCPU"
                    icon="mdi-plus"
                  />
                  <v-icon
                  @click="minusCPU"
                    icon="mdi-minus"
                  />
                </template>
              </v-text-field>
              </v-col>
              <v-col cols="4" >
                <v-select
                  v-model="zone" 
                  label="Zone"
                  :items="['Develop', 'Production']"
                  required
                  >
                </v-select>
              </v-col>
            </v-row>

        </v-form>
        </v-card-text>
        <v-card-actions class="bg-mea-light">     
          <v-spacer></v-spacer>
          <v-btn variant="flat" class="color-mea" @click="btnAddVm">Add</v-btn>
          <v-btn variant="flat" class="color-mea" @click="closeDialog">Cancel</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </template>
  
  <script>
  var numeral = require("numeral");
  export default {
    name: 'FormAddVm',

    data() {
      return {
        dialogAddVm: false,
        host_name: '',
        os: '',
        memmory: '2,048',
        zone: '',
        cpu_count: 2,
        disk: 100,
      };
    },    
    props: {
        msg: String
    },
    methods: {
      plusMemmory() {
        this.memmory = parseInt(numeral(this.memmory).format("0")) + 1024;
        this.memmory = numeral(this.memmory).format("0,0")
      },
      minusMemmory() {
        if(parseInt(numeral(this.memmory).format("0")) > 2048){
          this.memmory = parseInt(numeral(this.memmory).format("0")) - 1024;
          this.memmory = numeral(this.memmory).format("0,0")
        } 
      },
      plusCPU() {
        this.cpu_count = parseInt(numeral(this.cpu_count).format("0")) + 1;
        this.cpu_count = numeral(this.cpu_count).format("0,0")
      },
      minusCPU() {
        if(parseInt(numeral(this.cpu_count).format("0")) > 2){
          this.cpu_count = parseInt(numeral(this.cpu_count).format("0")) - 1;
          this.cpu_count = numeral(this.cpu_count).format("0,0")
        } 
      },
      plusDisk() {
        this.disk = parseInt(numeral(this.disk).format("0")) + 100;
        this.disk = numeral(this.disk).format("0,0")
      },
      minusDisk() {
        if(parseInt(numeral(this.disk).format("0")) > 100){
          this.disk = parseInt(numeral(this.disk).format("0")) - 100;
          this.disk = numeral(this.disk).format("0,0")
        } 
      },
      openDialog() {
        this.dialogAddVm = true;
      },
      closeDialog() {
        this.dialogAddVm = false;
      },
      btnAddVm() {
        this.requestVm()
        // Implement your user registration logic here
        //console.log('Registering user with the following details:');
        // Close the dialog after registration
        //this.closeDialog();
      },
      requestVm(){
        var axios = require('axios');
        var data = JSON.stringify({
          "hostname": this.host_name,
        });

      var config = {
        method: 'post',
        maxBodyLength: Infinity,
        url: 'http://localhost:5000/create_vm',
        headers: {
          'Content-Type': 'application/json',
          'accept': '*/*'
        },
        data: data,

      };
      axios(config)
        .then(function (response) {
          alert("deploymentId :"+response.data[0].deploymentId)
          //console.log(JSON.stringify(response.data));
        })
        .catch(function (error) {
          console.log(error);
        });
      
      }
    },
  };
  </script>
  