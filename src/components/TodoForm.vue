<template>

    <form action="" class="d-flex" @submit.prevent="onClick">
        <div class="flex-grow-1 me-2">
            <input 
            class="form-control"
            type='text'
            placeholder="할 일을 입력하세요"
            v-model="todo">
        </div>
        <div>
            <button type="submit" class="btn btn-primary">
                Add 
            </button>
        </div>
    </form> 
</template>

<script>

export default{
    setup(){
        return {

        }
    }   
}

</script>

<style>

</style>