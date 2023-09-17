<template>
  <v-divider class="my-2" :thickness="3"></v-divider>
    <v-form fast-fail @submit.prevent>
      <v-row>
        <v-col>
          <v-radio-group
            v-model="inline"
            inline
          >
          <v-label class="color-mea">Status : </v-label>
          <v-radio
            label="Approve"
            value="radio-1"
          ></v-radio>
          <v-radio
            label="Reject"
            value="radio-2"
          ></v-radio>
        </v-radio-group>
      </v-col>
      <v-col cols="6">
        <v-text-field
          v-model="Comment"
          label="Comment"
          :rules="CommentRules"
        ></v-text-field>
      </v-col>
      <v-col cols="2">
        <v-btn type="submit" block class="mt-2 color-mea">Submit</v-btn>
      </v-col>
      </v-row>
    </v-form>
</template>
  <script>
    export default {
      data: () => ({
        Comment: '',
        inline:'',
        CommentRules: [
          value => {
            if (value?.length > 3) return true
            return 'Comment must be at least 3 characters.'
          },
        ],

      }),
    }
  </script>