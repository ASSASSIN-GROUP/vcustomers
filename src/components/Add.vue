<template>
  <div class="add container">
    <h1 class="page-header">Add Customer</h1>
    <form v-on:submit="addCustomer">
        <div class="well">
            <h4>Customer Info</h4>
            <div class="form-group">
                <label>Name</label>
                <input type="text" class="form-control" placeholder="Input the Name" v-model="user.name" required/>
            </div>
        </div>
        <div class="well">
            <h4>Customer Contact</h4>
            <div class="form-group">                
                <label>Email</label>
                <input type="text" class="form-control" placeholder="Enter the Email" v-model="user.email" required/>
            </div>
            <div class="form-group">
                <label>Phone</label>
                <input type="text" class="form-control" placeholder="Enter the Phone" v-model="user.phone" />
            </div>
            <div class="form-group">
                <label>Company</label>
                <input type="text" class="form-control" placeholder="Enter the Company" v-model="user.company" required/>
            </div>
        </div>
        <div class="well">
            <h4>Customer Address</h4>
            <div class="form-group">
                <label>Street</label>
                <input type="text" class="form-control" placeholder="Enter the Street" v-model="user.street" required/>
            </div>
            <div class="form-group">
                <label>State</label>
                <input type="text" class="form-control" placeholder="Enter the State" v-model="user.suite" />
            </div>
            <div class="form-group">
                <label>City</label>
                <input type="text" class="form-control" placeholder="Enter the Address" v-model="user.city" required/>
            </div>
            <div class="form-group">
                <label>ZipCode</label>
                <input type="text" class="form-control" placeholder="Enter the ZipCode" v-model="user.zipcode" required/>
            </div>
        </div>
        <button class="btn btn-primary" v-on:click="adduser">Add Customer</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'add',
  data () {
    return {
        user: {

        }
    }
  },
  methods:{
      addCustomer:function(e){
        if(!this.user.name || !this.user.email){
            console.log("Please fill in all required fields");
        } else{
            let newuser = {
                name: this.user.name,
                phone: this.user.phone,
                email: this.user.email,
                street: this.user.address.street,
                state:this.user.address.suite,
                city: this.user.address.city,
                zipcode:this.user.address.zipcode,
                company: this.user.company.name
            }
            this.$http.post('https://jsonplaceholder.typicode.com/users/add', newuser)
            .then(function(reponse){
                this.$router.push({path: '/'});
            })
            e.preventDefault();
        }
        e.preventDefault();
      },
      adduser: function(){
          
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .add container {
        margin-left: 20px
    }
</style>