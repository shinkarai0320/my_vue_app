<template> 
    <div>
      <h1 :class="name">
        welcome to {{ name }}
      </h1>
      <h3>
        {{ greeting("kokkok") }}
      </h3>
      <div>
        <input type='text' v-model='name'>
      
          
      </div>

      <div>
        <input :type='type'>
        <button type="button" class="btn btn-primary"
          @click="updateName" 
        >
         
        Click
      </button>
      
    </div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue'

  export default {
    name: 'SampleComponent', // ✅ 단일 단어 X
  
    setup() {
      // setup 함수 내에서 사용할 변수와 함수를 정의
      const name = ref('VUEJS'); // 기본자료형, ref를 사용하여 반응형 변수 생성
      const type = ref('number');
      const cssName = ref('name');
      
      // 기본자료형, ref를 사용하여 반응형 변수 생성
      const greeting = (temp) => {
        return "Hello " + temp;
      }

      const updateName = (e) => {
        name.value = e.target.value; // ref를 사용하여 값 업데이트
        console.log(name.value);
      }
  
      return {
        name,
        type,
        cssName,
        greeting,
        updateName,
    
      }
    }
  }
  </script>
  
  <style>
  .name {
    color: purple;
  }

  .temp {

    color: rgb(188, 152, 226);
  }
  </style>
  