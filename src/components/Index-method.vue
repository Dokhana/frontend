<template>
<div>
    <h1>Method</h1>

    <table class="table table-hover">
        <thead>
        <tr>
            <td>ID</td>
            <td>arrivingArabicName</td>
            <td>arrivingEnglishName</td>
            <td>Sort</td>
        </tr>
        </thead>

        <tbody>
            <tr v-for="method in methods" :key="method._id">
                <td>{{ method._id }}</td>
                <td>{{ method.arabicname }}</td>
                <td>{{ method.englishname }}</td>
                <td>{{ method.sort }}</td>
                <td>Update</td>
                <td><router-link :to="{name: 'Update', params: { id: method._id }}" class="btn btn-primary">Update</router-link></td>
                    <td><button class="btn btn-danger"  v-on:click="deleteItem(method._id)">Delete</button></td>
                </tr>
        </tbody>
    </table>
</div>
</template>


<script>
export default {
    data(){
        return{
            methods: []
        }
    },

    mounted ()
    {
        this.fetchmethods();
    },

    methods: {
        async fetchmethods()
        {
        this.axios.get("http://40.127.194.127:777/api/Emergency/GetAllArrivingMethods?first=0&page=0&rows=10")
        .then(response => {
        this.methods = response.data;
        console.log(response.data);
        })
        .catch(error => {
          console.log(error);
        });
        },
        deleteMember(id)
            {
            this.axios.delete("http://40.127.194.127:777/api/Emergency/DeleteArrivingMethod", {
          id: id
        })
        .catch(error => {
          console.log(error);
        });
    }
}
}
</script>