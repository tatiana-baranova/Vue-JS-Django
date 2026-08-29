<template>
    <div class="header">
        <span class="logo">{{ title }}</span>
        <button @click="addRating">+</button>
        <span class="user">{{ fullName }} ({{ user.rating }})</span>
    </div>
</template>

<script>
export default {
    data(){
        return {
            user:{
                name: 'Anna',
                surname: 'Doe',
                age: 20,
                rating: 0,
                email: 'annadoe@gmail.com'
            },
            allRating: 0
        };
    },
    computed: {
        fullName(){
            return `Hello  ${this.user.name} ${this.user.surname}`
        },
    },
    methods:{
        addRating(){
            this.user.rating++;
            this.allRating++;
        },
    },
    mounted(){
        this.addRating()
    },
    watch:{
        allRating(newValue, oldValue){
            if(newValue > 5)
                console.log(`${newValue} - ${oldValue}`);
        }
    },
    props:{
        title:{
            type: String,
            required: true,
        }
    },


};
</script>
<style lang="css" scoped>
.header{
    background-color: #a6534afe;
    color: white;
    padding: 20px;
    border-bottom: 2px solid #443f3f;
}

.header .logo{
    font-size: 20px;
}
.header .user{
    float: right;
}
.header button{
    float: right;
    border: 0;
    color: rgb(255, 255, 255);
    background-color: #2f0303;
    border-radius: 5px;
    padding: 10px 15px;
    font-size: 12px;
    font-weight: bold;
    cursor: pointer;
    margin-left: 5px;
    position: relative;
    top: -5px;
}
.header button:hover{
    background-color: #d08d8d;
}
</style>
