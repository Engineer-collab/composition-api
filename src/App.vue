<template>
  <section class="container">
    <user-data :age="userAge" :firstName="firstName" :lastName="lastName"></user-data>
    <!-- <h2>{{ userName }}</h2>
    <h3>{{ userAge }}</h3> -->
    <button @click="setAge">Change Age</button>
    <div>
      
    <input type="text" placeholder="first name" v-model="firstName">
    <input type="text" placeholder="last name" ref="lastNameInput">
    <button @click="setLastName">Set Last Name</button>
    </div>
  </section>
  
  
</template>

<script>


import { ref,computed,watch  } from "vue";
import userData from "./components/userData.vue";
export default {
  components:{
    userData
  },
setup(){
//  const uName = ref('waqas wattu'); 
 const uAge = ref(31);
 const firstName = ref('');
 const lastName = ref('');
 const lastNameInput= ref(null)
  // const user = reactive({
  //   name : 'waqas wtu',
  //   age : 31
  // });
  function setNewAge(){
    uAge.value = 32
  } 
  function setLastName(){
  lastName.value = lastNameInput.value.value;
  }
  const uName = computed(function(){
  return firstName.value + ' ' + lastName.value;
  });
  watch([uAge,uName],function(newValue,oldValue){
  console.log('old age',oldValue[0])
  console.log('new age',newValue[0])

  console.log('old name',oldValue[1])
  console.log('new name',newValue[1])
  })
// function setfirstName(event){
//   firstName.value = event.target.value;
// }
// function setlastName(event){
//   lastName.value = event.target.value;
// }
 
  return{
    userName:uName,userAge:uAge,setAge:setNewAge,lastName,firstName:firstName,setLastName,lastNameInput
  }
}
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
  // },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>