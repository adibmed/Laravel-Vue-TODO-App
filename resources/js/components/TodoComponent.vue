<template>
    <div class="w-50">
        <form @submit.prevent="saveData">
            <div class="input-group mb-3 w-100">
                <input
                v-model="Form.title"
                    type="text"
                    class="form-control form-control-lg"
                    placeholder="Add Todo"
                    aria-label="Add Todo"
                    aria-describedby="button-addon2"
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
        </form>
    </div>
</template>

<script>
export default {
    data: () => {
        return {
            Form: new Form({
                title: '',
            })
        };
    },
    methods: {
        saveData(){
            let data = new formData();
            data.append('title', this.form.title);
            axios.post('/api/todo', data);
        }
    },
    mounted() {
        console.log("Component mounted.");
    }
};
</script>
