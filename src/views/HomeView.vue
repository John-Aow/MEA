<template>
  <div class="home">
    <v-container fluid>
      <v-row>
        <v-col>
          <v-card class="mx-auto my-3 d-flex flex-column" height="100%" max-width="344">
            <v-card-item class="bg-mea-light">
              <div>
                <div class="text-h6 mb-1">
                  Request Virtual Machine
                </div>
              </div>
            </v-card-item>
            <v-card-text>
              <v-list-item class="text-left" v-for="item in vm_items" :key="item.title" :title="item.title">
                <template v-slot:prepend>
                  <v-avatar>
                    <v-icon>mdi-circle-small</v-icon>
                  </v-avatar>
                </template>
              </v-list-item>
            </v-card-text>
            <v-spacer></v-spacer>
            <v-card-actions>
              <v-btn block class="color-mea" variant="outlined" to="/request_vm">
                Request
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
        <v-col>
          <v-card class="mx-auto my-3 d-flex flex-column" height="100%" max-width="344">
            <v-card-item class="bg-mea-light">
              <div>
                <div class="text-h6 mb-1">
                  Request Database
                </div>
              </div>
            </v-card-item>
            <v-card-text>
              <v-list-item class="text-left" v-for="item in database_items" :key="item.title" :title="item.title">
                <template v-slot:prepend>
                  <v-avatar>
                    <v-icon>mdi-circle-small</v-icon>
                  </v-avatar>
                </template>
              </v-list-item>
            </v-card-text>
            <v-spacer></v-spacer>
            <v-card-actions>
              <v-btn block class="color-mea" variant="outlined">
                Request
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>


export default {
  name: 'HomeView',
  components: {

  },
  data() {
    return {
      vm_items: [
        { title: "Windows 2019 Datacenter" },
        { title: "CentOS8" },
        { title: "Ubuntu 12" },
        { title: "Request up to 30 VMs" },
        { title: "vCenter Location" },
      ],
      database_items: [
        { title: "Oracle database 12c on exadata" },
        { title: "Yanawa / Rat Burana" },
        { title: "User / Password" },
      ],
    };
  },
  methods: {
    openDialogRequestVM() {
      // Access the dialog component using its reference and call the openDialog method
      this.HeaderDialogRequest = 'Create Request VM';
      this.$refs.DialogFormRequestVm.openDialog();
    },
    LoginVmVra() {

      var axios = require('axios');
      var config = {
        method: 'post',
        maxBodyLength: Infinity,
        url: 'http://localhost:5000/login_vra',
        headers: {
          'Content-Type': 'application/json',
          'accept': '*/*'
        },

      };
      axios(config)
        .then(function (response) {
          console.log(JSON.stringify(response.data));
        })
        .catch(function (error) {
          console.log(error);
        });
    },
    

    },
    mounted() {
    }

  }
</script>
