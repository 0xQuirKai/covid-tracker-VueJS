<template>
<div>
    <select @change="change" v-model="selected" class="form-select mt-10 block w-full border p-3 rounded mb-3">
    <option value="0">select</option>
    <option v-for="cou in countries" :value="cou.ID" > {{cou.Country}}</option>
    </select>
</div>
</template>

<script>

    export default {
        name : 'Country',
        props:['countries'],
        data(){
            return {
                selected : 0
            }
        },
        methods : {
            change (){
                const country = this.countries.find((item)=>item.ID===this.selected)
            
            this.$emit("get-country",country)
            }
        }

    }
</script>