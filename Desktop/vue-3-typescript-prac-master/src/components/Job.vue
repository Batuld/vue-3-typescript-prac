<template>
<div class="job-list">
    <p><b>Order By {{order}}</b></p>
<ul class="list-disc">
    <li v-for="job in orderItems" :key="job.id" class="text-left ... rounded overflow-hidden shadow-lg w-fit justify-center p-10">
    <h2 class=""><b>{{job.title}} in {{job.location}}</b></h2>
    <div>
        <p class="text-lime-500">{{job.salary}} rupees</p>
    </div>
    <div>
        <p>Understanding client requirements and how they translate to new application features
        Collaborating with development team and other IT staff to set specifications for new applications
        Writing high-quality code to program complete applications on schedule </p>
    </div>
    </li>
</ul>
</div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from 'vue';
import job from '../types/Jobs'
import orderTerms from '../types/orderTerms';

export default defineComponent({
    props:{
        jobs: {
            required: true,
            type: Array,
            default: []
        },
 
    order:{
         required: true,
            type: String as PropType<orderTerms>
    }
       },
        setup(props){
            const orderItems = computed(() => {
               return props.jobs.sort((a: job , b: job) =>{
               return a[props.order] > b[props.order] ? 1 : -1
            })
        })
       
        return { orderItems }
         }
})


</script>