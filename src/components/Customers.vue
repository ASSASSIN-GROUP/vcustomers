<template>
  <div class="customers container">
    <h1 class="page-header">Manage customers</h1>
    <table class="table table-striped">
      <thead>
        <tr>
          <th>No</th>
          <th>Name</th>
          <th>UserName</th>
          <th>Email</th>
          <th>Address</th>
          <th>Phone</th>
          <th>Company</th>  
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in customers">
          <td>{{user.id}}</td>
          <td>{{user.name}}</td>
          <td>{{user.username}}</td>
          <td>{{user.email}}</td>
          <td><strong>street:</strong>{{user.address.street}}<br/>
              <strong>state:</strong>{{user.address.suite}}</br>
              <strong>city:</strong>{{user.address.city}}</br>
              <strong>zipcode:</strong>{{user.address.zipcode}}
          </td>
          <td>{{user.phone}}</td>
          <td>{{user.company.name}}</td>
          <td>
            <button class="btn btn-success btn-xs">Edit</button>
            <button class="btn btn-danger btn-xs">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'customers',
  data () {
    return {
      customers: []
    }
  },
  methods: {
    fetchCustomers(){
      // this.$http.get('http://slimapp/api/customers')
      // .then(function(response){
      //   console.log(response.body);
      // });
    }
  },
  // created: function(){
  //   this.fetchCustomers();
  // }
  created: function(){
    // this.fetchCustomers();
    this.$http.get('https://jsonplaceholder.typicode.com/users')
      .then(function(response){
        // this.customers = JSON.parse(response.body);
        this.customers = response.data;
      });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  /*.customers container {
    margin-left: 20px
  }*/
</style>
