<template>
    <div 
        id="some-id"
        class="my-class"
    >
        {{ message }} <br> {{ message2 }}
        <br>
        <div class="container">
            <div class="row">
              <div class="col-lg-12">
                <table class="table table-bordered table-striped">
                  <thead>
                    <tr class="text-center bg-info text-light">
                      <!-- <th>ID</th> -->
                      <th>Name</th>
                      <th>Email</th>
                      <th>Phone</th>
                      <th>DOB</th>
                      <th>Subject</th>
                      <th>Edit</th>
                      <th>Delet</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr class="text-center" v-for="(item, idx) in items" :key="idx">
                      <!-- <td>{{ item._id }}</td> -->
                      <td>{{ item.name }}</td>
                      <td>{{ item.email }}</td>
                      <td>{{ item.pho }}</td>
                      <td>{{ item.dob }}</td>
                      <td>{{ item.sub }}</td>
                      <td><a href="#" class="text-success"><i class="fas fa-edit"></i></a></td>
                      <td><a href="#" class="text-danger" @click="removeItem(item)" ><i class="fas fa-trash-alt"></i></a></td>
                    </tr>
                   
                  </tbody>
                </table>
              </div>
            </div>
            <!--End Show data from MongoDB-->
            <div class="modal-dialog">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title">Add New Student</h5>
                        <button type="button" class="close" ><span aria-hidden="true">&times;</span></button>
                    </div>
                    <div class="modal-body p-4">
                        
                        <form @submit.prevent="saveNewItem">
                            <div class="form-group">
                                <input
                                    type="text" 
                                    class="form-control form-control-lg"
                                    placeholder="Name"
                                    id="item-name"
                                    v-model="item.name"
                                >
                            </div>
                            <div class="form-group">
                                <input
                                    type="email"
                                    name="email" 
                                    class="form-control form-control-lg" 
                                    placeholder="Email"
                                    id="item-email"
                                    v-model="item.email"
                                >
                            </div>
                            <div class="form-group">
                                <label for="item-pho">Phone number:</label>
                                <input 
                                    type="tel" 
                                    name="phone" 
                                    class="form-control form-control-lg"
                                    id="item-pho"
                                    v-model="item.pho"
                                >
                            </div>
                            <div class="form-group">
                                <label for="item-dob">Date of Barth</label>
                                <input 
                                    type="date" 
                                    name="dob" 
                                    class="form-control form-control-lg"
                                    id="item-dob"
                                    v-model="item.dob"
                                >
                            </div>
                            <div class="form-group">
                              <label for="item-sub">Subject</label>
                              <input 
                                type="text" 
                                name="sub" 
                                class="form-control form-control-lg" placeholder="Enter Subject"
                                id="item-sub"
                                v-model="item.sub"
                              >  
                            
                            </div>
                            <div class="form-group">
                                <button class="btn btn-info btn-block btn-lg">Add User</button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>

        </div>


    </div>
</template>

<script>
    import { Items } from "/imports/api/items";

    w_items = Items;


    export default {
        
        data() {
            return { 
                message: 'Hello YouTube !',
                message2: 'Subsoribe',
                item: { name: '', email: '', pho: 0, dob: '', sub: '' } 
                };
        },
        computed: {
            myComputed() {
                let undef = 4;
                return undef;
            },
        },
        methods: {
            saveNewItem() {
                Items.insert(this.item);
            },
            removeItem(item) {
                Items.remove({ _id: item._id });
            }
        },
        meteor: {
            items() {
                return Items.find({}).fetch()
            }
        }
        
    };
</script>

<style lang="css" scoped>
    
</style>