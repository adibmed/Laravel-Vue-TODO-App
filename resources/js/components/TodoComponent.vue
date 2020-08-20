<template>
    <div class="w-50">
        <form @submit.prevent="saveData">
            <div class="input-group mb-3 w-100">
                <input
                    v-model="form.title"
                    type="text"
                    class="form-control form-control-lg"
                    placeholder="Add Todo"
                    aria-label="Add Todo"
                    aria-describedby="button-addon2"
                   :class="{'is-invalid' : form.errors.has('title')}"
                />
          
                <div class="input-group-append">
                    <button
                        class="btn btn-success"
                        type="submit"
                        id="button-addon2" 
                    >
                        ADD TODO
                    </button>
                </div>
            </div>
                  <span 
                v-if="form.errors.has('title')"
                v-text="form.errors.get('title')"
                class="text-danger pt-3"
                >

                </span>
        </form>
        <div class="w-25">
            <div 
            v-for="todo in todos" 
            v-bind:key="todo.id"
            class="w-100">
                    {{ todo.title }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data: () => {
        return {
            form: new Form({
                title: '',
            }),
            todos: []
        };
    },
    methods: {
        getTodos() {
            axios.get('/api/todo')
            .then((res)=>{
                this.todos = res.data;
            })
            .catch(error => {
                console.log(error);
            })
        },
        saveData(){
            let data = new FormData(); 
            data.append('title', this.form.title);
   
            axios.post('/api/todo', data)
            .then((res)=>{
                console.log("✅ Todo added successfully");
                this.form.reset();
                this.getTodos();
            }
            )
            .catch((error) => {
                this.form.errors.record(error.response.data.errors);
                console.log("💔 " + error)
            })
        } 
            

    },
    mounted() {
        console.log("🔥 Component mounted. 🚀");
        this.getTodos();
    }
};
</script>
