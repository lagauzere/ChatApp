<script setup>
import { computed } from 'vue';
import {TrashIcon} from '@heroicons/vue/24/outline'

    const props = defineProps({
        message: {
            type: Object,
            required: true
        }
    })

    const emit = defineEmits(['delete','update']);

    const formatDate = (date) => {
        let formatedDay= date.toLocaleDateString();
        let formatedTime = date.toLocaleTimeString('default',{hour: '2-digit', minute: '2-digit'})
        return `${formatedDay} à ${formatedTime}`
    }

    const formatedDate= computed(()=>{
        const date =  props.message.date

    return formatDate(date)
    })


</script>


<template>
    <div class="mt-8">
        <div class=" flex align-center">
            <img class=" h-14 w-14 rounded-full mr-4" :src="message.user.avatarUrl" alt="avatar perso">
            <p v-text="message.user.username"></p>
        </div>
       
      {{ formatedDate }}
      <button @click="emit('delete',message.id)" class="bg-red-500 rounded-full p-1 hover:bg-red-300">
       <TrashIcon class=" w-5 h-5"></TrashIcon> 
      </button>
        <p class="" v-text="message.text"></p>
    </div>
    
</template>