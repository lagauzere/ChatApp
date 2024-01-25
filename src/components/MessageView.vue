<script setup>
import { computed } from 'vue';

    const props = defineProps({
        message: {
            type: Object,
            required: true
        }
    })

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
        <p class="" v-text="message.text"></p>
    </div>
    
</template>