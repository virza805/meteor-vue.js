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
                      <td><a href="#" class="text-success" ><i class="fas fa-edit"></i></a></td>
                      <td><a href="#" class="text-danger" ><i class="fas fa-trash-alt"></i></a></td>
                    </tr>
                   
                  </tbody>
                </table>
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
            return { message: 'Hello YouTube !', message2: 'Subsoribe' };
        },
        computed: {
            myComputed() {
                let undef = 4;
                return undef;
            },
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