<template>
        <main>
            <div v-if="articles.length > 0" id="articles">
            <div class="post" v-for="el in articles" :key="el.id">
                <button @click="deletePost(el.id)">Delete</button>
                <h2>{{ el.title }}</h2>
                <p>{{ el.text }}</p>
            </div>
        </div>
        <h1 class="empty" v-else> Статті відсутні на даний момент</h1>
        </main>
        <aside>
            <AddPost v-on:add-post="createPost"/>
        </aside>
</template>

<script>
import AddPost from './AddPost.vue';
export default{
    name:'Articles',
    components: {
        AddPost,
    },
    data(){
        return{
            articles:[
                {
                    "id": 1,
                    "title": "Секрети майстерні Стівена Кінга",
                    "text": "Відомий письменник вважає регулярну працю основою свого успіху. Він щодня пише щонайменше дві тисячі слів без жодних винятків."
                },
                {
                    "id": 2,
                    "title": "Феномен популярності Джоан Роулінг",
                    "text": "Історія створення всесвіту Гаррі Поттера надихає мільйони людей по всьому світу. Авторка пройшла складний шлях від бідності до світового визнання."
                },
                {
                    "id": 3,
                    "title": "Творчий метод Ернеста Гемінґвея",
                    "text": "Класик американської літератури віддавав перевагу лаконічному та простому стилю написання. Його принцип айсберга назавжди змінив підходи до сучасної прози."
                },
                {
                    "id": 4,
                    "title": "Особливості уяви Джорджа Мартіна",
                    "text": "Творець відомого фентезі-всесвіту приділяє величезну увагу деталізації своєї вигаданої історії. Він детально прописує кожну династію та навіть меню на королівських бенкетах."
                },
                {
                    "id": 5,
                    "title": "Детективна логіка Агати Крісті",
                    "text": "Королева детективу вигадувала заплутані сюжети під час миття посуду або впорядкування саду. Її персонажі Еркюль Пуаро та місс Марпл стали еталонами світового жанру."
                }
            ]
        }
    },
    methods: {
        deletePost(id){
            this.articles = this.articles.filter(el => el.id !== id)
        },
        createPost(userTitleInput, userTextInput){
                this.articles.unshift({
                    id: this.articles.length +1,
                    title: userTitleInput,
                    text: userTextInput
                });

        },
    },
}
</script>

<style scoped>
main{
    float: left;
    width: 60%;
}
aside{
    float: left;
    width: 20%;
    margin-left: 10%;
}
#articles{
    margin: 20px;
}

#articles .post{
    background-color: rgba(234, 169, 169, 0.691);
    padding: 20px;
    margin-bottom: 20px;
    border: 1px solid #2f0b0b;
    color: #494646;
    float: left;
    width: 100%;
}
#articles button,
aside form button{
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
#articles button:hover,
aside form button:hover{
    margin-top: 2px;
    border-bottom-width: 2px;

}
.empty{
    margin: 20px;
    color: #494646;
}


</style>
