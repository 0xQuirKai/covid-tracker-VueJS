<template>
    <div class="text-center">
         <h2 class="text-3xl font-bold ">{{text}}</h2>
    <div class="text-2xl mt-4 mb-10">{{time}}</div>
    
    </div>
</template>
<script>
import moment from 'moment'
export default {
    name : 'Data',
    props : ['text','dataDate'],
computed:{
time:function(){
    return moment(this.dataDate).format('Do MMMM YYYY  ,  h:mm:ss a')
}
}
}
</script>