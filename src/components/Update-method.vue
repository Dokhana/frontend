<template>
<div class="container">
    <div class="card">
        <div class="card-header">
            <h3>Edit Method</h3>
        </div>
        <div class="card-body">
            <form v-on:submit.prevent="updateMethod">
                <div class="form-group">
                        <label>arrivingArabicName:</label>
                        <input type="text" class="form-control" v-model="method.arabicname"/>
                    </div>

                    <div class="form-group">
                        <label>arrivingEnglishName:</label>
                        <input type="text" class="form-control" v-model="method.englishname"/>
                    </div>

                    <div class="form-group">
                        <label>sort:</label>
                        <input type="number" class="form-control" v-model="method.sort"/>
                    </div>

                    <div class="form-group">
                        <input type="submit" class="btn btn-primary" value="Update Method"/>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    data(){
        return{
            method:{arabicname:"",
                    englishname:"",
                    sort:""}
        }
    },

    mounted() {
        this.getMethod();
    },

    methods: {
           async getMethod()
            { this.axios
        .post("http://40.127.194.127:777/api/Emergency/GetAllArrivingMethods?first=0&page=0&rows=10", {
          id: this.$route.params.id
        })
        .then(response => {
          this.method = response.data;
          console.log(response.data);
        })
        .catch(error => {
          console.log(error);
        });
    },

       async updateMethod()
        { this.axios.put("http://40.127.194.127:777/api/Emergency/AddOrUpdateArrivingMethod" , {
            id: this.$route.params.id,
            arabicname: this.method.arabicname,
            englishname: this.method.englishname,
            sort: this.method.sort
        });
       //this.$router.push({name: 'Index'}); 
    }
}
}

</script>