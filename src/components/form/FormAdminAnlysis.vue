<template>
  <v-card class="mx-auto my-2" >
    <v-card-title class="color-mea">Cloud Admin</v-card-title> 
    <v-table density="compact">
      <thead>
        <tr>
          <th class="text-left">No.</th>
          <th class="text-left">Question</th>
          <th class="text-left">Point</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(item, index)  in questions"
          :key="item.id"
        >
          <td>
            <v-checkbox
              :model-value="false"
            > {{ index + 1 }}
          </v-checkbox>  
          </td>

          <td>{{ item.question }}</td>
          <td>{{ item.point }}</td>
        </tr>
      </tbody>
    </v-table>
    <v-card-actions><v-btn type="submit" block class="mt-2 color-mea">Submit</v-btn></v-card-actions>
    
  </v-card>

</template>
<script>
  export default {
    data: () => ({
      questions:[
        {
          id: 1,
          question:'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
          point: 5
        },
        {
          id: 2,
          question:'Sed vestibulum sapien eu lectus interdum, ac fermentum erat dignissim',
          point:5
        },
        {
          id: 3,
          question:'Donec elementum leo varius velit auctor sagittis et a dolor.',
          point: 5
        },
        {
          id: 4,
          question:'Proin malesuada risus at ligula viverra, a placerat tellus rutrum.',
          point: 5
        },
      ],
      
    }),
  }
</script>