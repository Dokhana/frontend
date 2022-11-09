<template>
<div class="container">
    <div class="card">
        <div class="card-header">
            <h3>Add Method</h3> 
        </div>
        <div class="card-body">
            <form v-on:submit.prevent="addMethod">
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
                        <input type="submit" class="btn btn-primary" value="Add Method"/>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
data() {
      return {
          method: { arabicname:"",
                    englishname:"",
                    sort:""}
      }
  },
  methods: {
     async addMethod() {
        await this.axios.post("http://40.127.194.127:777/api/Emergency/AddOrUpdateArrivingMethod" , 
        {
        arabicname: this.method.arabicname ,
        englishname: this.this.method.englishname,
        sort: this.this.method.sort
    });
    }
}}
</script>