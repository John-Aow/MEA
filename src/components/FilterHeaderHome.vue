<template>
    <v-row no-gutters>
      <v-col>
        <v-sheet class="pa-2 ma-2">
            <v-text-field v-model="filter_request_id" label="Request ID"></v-text-field>
        </v-sheet>
      </v-col>
      <v-col>
        <v-sheet class="pa-2 ma-2">
            <v-text-field v-model="filter_project_name" label="Project Name"></v-text-field>
        </v-sheet>
      </v-col>
      <v-col>
        <v-sheet class="pa-2 ma-2">
            <v-select
                v-model="filter_status" 
                label="Status Request"
                :items="['Open', 'Waiting', 'Approve', 'Reject','In Queue', 'Complete', 'Not Complete']"
            ></v-select>
        </v-sheet>
      </v-col>
    </v-row>
</template>

<script>
export default {
    name: 'FilterHeaderHome',
  
    data() {
      return {
        filter_request_id: '',
        filter_project_name: '',
        filter_status: '',
      };
    },
}
</script>
