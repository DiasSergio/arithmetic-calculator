<script setup>

const props = defineProps(['editFirstValue', 'editSecondValue', 'editFilter'])

</script>

<template>
    <form>
        <div class="row inputs">
            <div class="col-md-4">
                <input required @keyup="props.editFirstValue" type="number" placeholder="Enter your first value"
                    class="form-control">
            </div>
            <div class="col-md-3">
                <select @change="props.editFilter" class="form-control">
                    <option value="Math">
                        Do the math!
                    </option>
                    <option value="Addition">
                        Addition
                    </option>
                    <option value="Subtraction">
                        Subtraction
                    </option>
                    <option value="Division">
                        Division
                    </option>
                    <option value="Multiplication">
                        Multiplication
                    </option>
                </select>
            </div>
            <div class="col-md-4">
                <input required @keyup="props.editSecondValue" type="number" placeholder="Enter your second value"
                    class="form-control">
            </div>
        </div>
    </form>
</template>

<style scoped>
.inputs {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
}

input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0
}
</style>