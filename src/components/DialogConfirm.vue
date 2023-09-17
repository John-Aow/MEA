<template>
  <v-row justify="center">
    <v-dialog v-model="dialogConfirm" persistent width="auto">

      <v-card>
        <v-card-title class="text-h5">
          {{ title }}
        </v-card-title>
        <v-card-text>{{ msg }}</v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="green-darken-1" variant="text" @click="closeDialog">
            Confirm
          </v-btn>
          <v-btn color="green-darken-1" variant="text" @click="closeDialog">
            Cancel
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>
<script>
export default {
  data() {
    return {
      dialogConfirm: false,
    }
  },
  props: {
    msg: String,
    title: String,
  },
  methods: {
    openDialog() {
      this.dialogConfirm = true;
    },
    closeDialog() {
      this.dialogConfirm = false;
    },

  },
}
</script>