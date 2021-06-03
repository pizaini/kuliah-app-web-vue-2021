<template>
  <div>
    <div class="app-page-title">
      <div class="page-title-wrapper">
        <div class="page-title-heading">
          <div class="page-title-icon">
            <i class="pe-7s-car icon-gradient bg-mean-fruit">
            </i>
          </div>
          <div>Customers
            <div class="page-title-subheading">This is an example dashboard created using build-in elements and components.
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-12">
        <div class="main-card mb-3 card">
          <div class="card-body">
            <h5 class="card-title">FORM Customer</h5>
            <form class="" @submit.prevent="submitFormCustomer">
              <div class="position-relative form-group"><label for="nama" class="">Nama</label><input name="nama" id="nama" placeholder="Nama customer" type="text" class="form-control"></div>
              <div class="position-relative form-group"><label for="email" class="">Email</label><input name="email" id="email" placeholder="Email customer" type="email" class="form-control">
              </div>
              <button class="mt-2 btn btn-primary">Save</button>
            </form>
          </div>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-12">
        <div class="main-card mb-3 card">
          <div class="card-body"><h5 class="card-title">Table with hover</h5>
            <table class="mb-0 table table-hover">
              <thead>
              <tr>
                <th>#</th>
                <th>ID</th>
                <th>Customer</th>
                <th>Email</th>
              </tr>
              </thead>
              <tbody>
              <tr v-for="(item, index) in dataCustomer" :key="item.id">
                <th scope="row">{{index + 1}}</th>
                <td>{{item.id}}</td>
                <td>{{item.nama}}</td>
                <td>{{item.email}}</td>
              </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
//axios.defaults.headers.common["X-Requested-With"]="XMLHttpRequest"
export default {
  name: "Menu1",
  data(){
    return {
      dataCustomer: []
    }
  },
  mounted() {
    this.loadData()
  },
  methods:{
    loadData(){
      axios.get("http://pabw-api.tif.localhost/customer")
          .then(response => {
            console.log(response);
          }).catch(error => {
            console.log(error)
      }).finally({

      })
    },
    submitFormCustomer(){
      const article = { title: "Vue POST Request Example" };
      axios.post("http://pabw-api.tif.localhost/customer/save", article)
          .then(response => {
            console.log(response)
      }).catch(error => {
        console.log(error)
      }).finally({

      })
    }
  }
}
</script>

<style scoped>

</style>