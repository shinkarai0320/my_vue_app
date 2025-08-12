<template>
    <!-- v-if vs v-show -->
     <!-- <div v-show="toggle">true</div>
     <div v-show="toggle">false</div> -->
    <div class ="container">
        <H2>Todo List</H2>

        <TodoForm /> <!-- TodoForm 컴포넌트 사용 -->

        <div v-show="toggle" class="alert alert-danger mt-2 p-2">
            ERROR : 할 일을 입력하세요
        </div>
        <div
            v-for="(td, index) in todos"
            :key="td.id"
            class="card mt-2">

            <div class="card-body p-2 d-flex align-items-center justify-content-between">
                <div class="form-check">
                    <input 
                        type="checkbox" 
                        class="form-check-input"
                        v-model="td.finish">
                    <label class="form-check-label"
                        :class="{'todo': td.finish}">

                        {{ td.todoWork }}
                    </label>
                 </div>
                    <button type="button" class="btn btn-outline-danger"
                        @click="todoDelete(index)"
                        >
                            Delete
                    </button>
                        
            </div>
            <!-- {{ todos }} -->
        </div>
    </div>    
    </template>

<script>
import { ref } from 'vue'
import TodoForm from './TodoForm.vue'   


  export default {
    components: {
        TodoForm // TodoForm 컴포넌트 등록
    },
    setup() {
        const toggle = ref(false);
        const todo = ref("");
        const todos = ref([
            { id: 1, todoWork: "homework", finish: false },
            { id: 2, todoWork: "play", finish: false },
            { id: 3, todoWork: "study", finish: false } //ture면 체크박스에 체크가 들어감
        ]);

        const onClick = () => {

            if (todo.value === '') {
                toggle.value = true;
            }else {
                toggle.value=false;
                todos.value.push({
                    id : Date.now(),
                    todoWork : todo.value
                })
                todo.value = ''; // 입력 후 초기화
                console.log(todos.value);
            }
        }

        const todoDelete = (index) => {

            console.log("delete : " + index);
            todos.value.splice(index, 1); // 해당 인덱스의 todo 삭제1
        
        }
            return {
                toggle,
                todo,
                todos,
                onClick,
                todoDelete
                }
            }
         }

</script>

<style>
    .todo{
        color: rgb(173, 114, 185);
        text-decoration: line-through;
}
</style>