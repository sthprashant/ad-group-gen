<template>
  <v-container>
    <div class="generated-table">
      <v-simple-table height="300">
        <thead>
          <tr>
            <th class="text-center">
              ID
            </th>
            <th class="text-center">
              AD Groups
            </th>
            <th class="text-center">
              Comments
            </th>
          </tr>
        </thead>
        <tbody class="text-center">
          <tr>
            <td>
              ipss
            </td>
            <td>
              AD group 1
            </td>
            <td>
              Test AD1
            </td>
          </tr>
          <tr>
            <td>
              ipss
            </td>
            <td>
              AD group 2
            </td>
            <td>
              Test AD2
            </td>
          </tr>
          <tr>
            <td>
              ipss
            </td>
            <td>
              AD group 3
            </td>
            <td>
              Test AD3
            </td>
          </tr>
        </tbody>
      </v-simple-table>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "generated-table"
};
</script>
