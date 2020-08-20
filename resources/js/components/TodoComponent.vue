<template>
    <div class="w-50">
        <form>
            <div class="input-group mb-3 w-100">
                <input
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
        return {};
    },
    mounted() {
        console.log("Component mounted.");
    }
};
</script>
