<script setup>
    import message from '@/components/MessageView.vue'
    import {ref} from 'vue'
    const messageText = ref('')

    const messageList= ref([])
    
function addMessage( ){
    //ajouter notre message à la  liste de message
    messageList.value.push({
        id: Math.random().toString(32).slice(2) ,
        text:messageText.value,
        date: new Date(),
        user:{
            username:'snacki',
            avatarUrl:'https://www.lemans.org/media/cache/api_news_large/assets/fileuploads/60/d4/60d43801a1971.jpg'
        }
    })
    messageText.value=''
  //  message.value.focus()
   
}


function deleteMessage(id){
    messageList.value = messageList.value.filter((message)=>message.id!==id);
}


</script>


<template>
    <div class="bg-orange-400">Chat App</div>

    <div v-for="(message,index) in messageList" class="mt-4" :key="index">
        
        <message @delete="deleteMessage" :message="message"></message>

    </div>


    <div class=" flex align-center">

    <textarea @keyup.enter.exact="addMessage" v-model="messageText" class="bg-orange-300 rounded-tm mt-4" name="message" id="message" cols="30" rows="2"></textarea>
    <button   @click="addMessage" class="p-2 bg-green-300 rounded-tm ml-4 mt-4" >Envoyer</button>
    </div>
</template>