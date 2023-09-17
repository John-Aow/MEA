<template>
    <v-table density="compact">
      <thead>
        <tr>
          <th class="text-left">No.</th>
          <th class="text-left">Position</th>
          <th class="text-left">Name</th>
          <th class="text-left">Date</th>
          <th class="text-left">Day</th>
          <th class="text-left">Status</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(item, index)  in flow_approve"
          :key="item.name"
        >
          <td>{{ index + 1 }}</td>
          <td>{{ item.position }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.date }}</td>
          <td>{{ item.day }}</td>
          <td>{{ item.status }}</td>
        </tr>
      </tbody>
    </v-table>
  </template>
  <script>
    export default {
      data () {
        return {
          flow_approve: [
            {
              name: 'Panumas',
              position: 'Requester',
              day: '-',
              date: '2023-07-23',
              status: '-',
            },
            {
              name: 'User Approve',
              position: 'Approval Lavel 3',
              day: '< 1 ',
              date: '2023-07-23',
              status: 'Approve',
            },
            {
              name: 'Admin',
              position: 'Cloud Admin',
              day: '4',
              date: '2023-07-30',
              status: 'Waiting',
            },
            
          ],
        }
      },
    }
  </script>