<template>
  <div class="holder">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <h1>Products</h1>
          <button
                    type="button"
                    class="btn btn-success add-btn"
                    data-bs-toggle="modal"
                    data-bs-target="#addProductModal"
                  >
                    Add
                  </button>
        </div>
        <div class="col">
          <table class="table is-striped is-bordered mt-5">
            <thead>
              <tr>
                <th>#</th>
                <th>Product Name</th>
                <th>Price</th>
                <th>Category</th>
                <th>Quantity</th>
                <th>Image</th>
                <th>Edit/Delete</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in product" :key="item.id">
                <td>{{ item.id }}</td>
                <td>{{ item.prodName }}</td>
                <td>{{ item.price }}</td>
                <td>{{ item.category }}</td>
                <td>{{ item.prodQuantity }}</td>
                <td><img class="tableImg" :src="item.imgURL" alt="" /></td>
                <td>
                  <button
                    type="button"
                    class="btn btn-primary"
                    data-bs-toggle="modal"
                    data-bs-target="#editProductModal"
                  >
                    Edit
                  </button>
                  <button class="btn btn-danger">Delete</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      <div class="row">
        <div class="col-12">
          <h1>Users</h1>
          <button
                    type="button"
                    class="btn btn-success add-btn"
                    data-bs-toggle="modal"
                    data-bs-target="#addUserModal"
                  >
                    Add
                  </button>
        </div>
        <div class="col">
          <table class="table is-striped is-bordered mt-5">
            <thead>
              <tr>
                <th>#</th>
                <th>FirstName</th>
                <th>LastName</th>
                <th>Gender</th>
                <th>CellNumber</th>
                <th>Email</th>
                <th>Role</th>
                <th>Join Date</th>
                <th>Image</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in user" :key="item.userID">
                <td>{{ item.userID }}</td>
                <td>{{ item.firstName }}</td>
                <td>{{ item.lastName }}</td>
                <td>{{ item.gender }}</td>
                <td>{{ item.cellphoneNumber }}</td>
                <td>{{ item.emailAdd }}</td>
                <td>{{ item.userRole }}</td>
                <td>{{ item.joinDate }}</td>
                <td><img class="tableImg" :src="item.userProfile" alt="" /></td>
                <td>
                  <button
                    type="button"
                    class="btn btn-primary"
                    data-bs-toggle="modal"
                    data-bs-target="#editUserModal"
                  >
                    Edit
                  </button>
                  <button class="btn btn-danger">Delete</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "admin-Comp",
  data() {
    return {
      product: [],
      user: [],
    };
  },
  created() {
    this.getProducts();
    this.getUsers();
  },
  methods: {
    async getProducts() {
      try {
        const response = await axios.get(
          "https://connections4u.onrender.com/products"
        );
        this.product = response.data.results;
        console.log(response);
      } catch (err) {
        console.log(err);
      }
    },

    async getUsers() {
      try {
        const response = await axios.get(
          "https://connections4u.onrender.com/users"
        );
        this.user = response.data.results;
        console.log(response);
      } catch (err) {
        console.log(err);
      }
    },

    async deleteProduct(id) {
      try {
        await axios.delete(`https://connections4u.onrender.com/products/${id}`);
        this.getProducts();
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style scoped>
.tableImg {
  height: 100px;
  width: 100px;
  border-radius: 25%;
  object-fit: contain;
}

.row {
  width: 70rem;
}

.add-btn{
  float: left;
}


</style>