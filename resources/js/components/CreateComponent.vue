<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Create New Student</div>

                    <div class="card-body">
                       <form name="myform" action="./api/student" method="POST" @submit.prevent="addStudent() " id="myform">
                        <div class="mb-3">
						    <label for="firstname" class="form-label">First Name</label>
						    <input type="text" v-model="student.firstname" class="form-control" id="firstname" >
						  </div> 
						  <div class="mb-3">
						    <label for="lastname" class="form-label">Last Name</label>
						    <input type="text" v-model="student.lastname" class="form-control" id="lastname" >
						  </div>
						  <div class="mb-3">
						    <label for="email" class="form-label">Email address</label>
						    <input type="email" v-model="student.email" class="form-control" id="email" aria-describedby="emailHelp">
						  </div>
						  <button type="submit"  class="btn btn-primary">Submit</button>
						</form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
    	data(){
    		 return {
                student: {
                  firstname:'',
                  lastname:'',
                  email:'',
                }
            }
    	},
    	mounted() {
            console.log('Component mounted.')
        },
       methods : {   
       		addStudent(){
       			        this.axios
                    .post('./api/student', this.student)
                    .then(response => (
                        this.$router.push({ name: 'home' })
                    ))
                    .catch(err => console.log(err))
                    .finally(() => this.loading = false)
       		}
       } 
    }
</script>

