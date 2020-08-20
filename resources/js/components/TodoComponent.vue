<template>
    <div>
        <form>
            <div class="input-group mb-3">
                <input
                    type="text"
                    class="form-control"
                    placeholder="Recipient's username"
                    aria-label="Recipient's username"
                    aria-describedby="button-addon2"
                />
                <div class="input-group-append">
                    <button
                        class="btn btn-outline-secondary"
                        type="button"
                        id="button-addon2"
                    >
                        Button
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
