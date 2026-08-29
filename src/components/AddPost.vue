<template>
    <form @submit.prevent="createPost" :class="{error: maxCharacters > 20}">
                <label for="title">Назва статті: </label>
                <input v-model="userTitleInput" type="text" placeholder="Введіть текст" id="title"/>
                <label for="title">Основний текст: <span>{{ maxCharacters }} / 20</span></label>
                <textarea v-model="userTextInput" type="text" placeholder="Введіть текст"></textarea>
                <button>Додати</button>
            </form>
</template>

<script>
export default{
    name:'AddPost',
    data(){
        return{
            userTitleInput:'',
            userTextInput: '',
        }
    },
    methods: {
        createPost(){
            if(this.userTitleInput !== "" && this.userTextInput !==""){
                this.$emit('add-post', this.userTitleInput, this.userTextInput)
                this.userTitleInput = "";
                this.userTextInput = "";
            }
        },
    },
    computed: {
        maxCharacters(){
            return this.userTextInput.length
        }
    }
}
</script>

<style scoped>
form{
    margin-top: 20px;
}
form label{
    color: #505050
}
form input,
form textarea{
    width: 100%;
    background-color: rgba(240, 232, 232, 0.814);
    border-radius: 5px;
    border: 2px solid #2f0b0b;
    padding: 8px 10px;
    font-style: 14px;
    color: #494646;
    outline: none;
    margin-bottom: 10px;
    resize: none;
}
form.error label{
    color: #c70909;
}
form button{
    float: right;
    background-color: #d27070;
    border: 2px solid #320707;
    border-bottom-width: 4px;
    padding: 8px 10px;
    font-weight: 600;
    color: #2f0b0b;
    border-radius: 5px;
    font-size: 14px;
    cursor: pointer;
}
form button:hover{
    margin-top: 2px;
    border-bottom-width: 2px;

}
</style>
