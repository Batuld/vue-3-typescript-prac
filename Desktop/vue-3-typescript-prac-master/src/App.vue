<template>
  <div>
    <button @click="handleClick('title')" class="flex-1 bg-gray-400 rounded p-1 m-2">Order by Title</button>
     <button @click="handleClick('location')" class="flex-1 bg-gray-400 rounded p-1 m-2">Order by Location</button>
      <button @click="handleClick('salary')" class="flex-1 bg-gray-400 rounded p-1 m-2">Order by Salary</button>
     <job :jobs ="jobs" :order="order"/>
  </div>
  
</template>

<script lang="ts">
import { defineComponent, ref , reactive, toRefs } from "vue";
import job from './components/Job.vue'
import jobts from './types/Jobs'
import orderTerms from './types/orderTerms'

export default defineComponent({
  //normal vue 2

  // data() {
  //   return {
  //     name: 'link',
  //     age: 25 as  string | number
  //   }
  // },

// with reactive

components:{job},
  setup(){
    // const state = reactive({
    //   name: 'link',
    //   age: 25 as string | number
    // })
    //  state.name = 'jgf'
    //  state.age='26'

    //  return {...toRefs(state)}

    // const name = ref('link')
    // const age = ref <Number | String>(25)

    // return{name,age}
    const jobs = ref<jobts[]>([
      { title: 'HR', location:'Pune', salary:30000, id:'1' },
      { title: 'QA', location:'Mumbai', salary:80000, id:'2' },
      { title: 'DevOps', location:'Banglore', salary:17000, id:'3' },
      { title: 'Software Developer', location:'Ahemdabad', salary:40000, id:'4' },
      { title: 'BDE', location:'Indore', salary:20000, id:'5' },
    ])

    const order = ref<orderTerms> ('title')

    const handleClick = (term: orderTerms ) => {
      order.value = term
    }
    return {jobs, handleClick, order}
  },

  methods:{
    // changeName(name : string) {
    // this.name = name
    // },
    // changeAge(age: string | number){
    //   this.age =  age
    //   return age
    // }
  }
});
</script>
<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
