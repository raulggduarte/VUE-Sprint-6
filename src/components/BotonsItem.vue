<template>
    <div>
        <button @click="$emit('selectItem','prev')">
            Anterior
        </button>
        <button @click="$emit('selectItem','next')">
            Següent
        </button>
    </div>
</template>
  
  
<script>

export default {
    name: 'BotonsItem',
}
</script>
  

<style scoped lang="scss">
    div {
        display: flex;
        
        & button {
            width: 500%;
            height: 50px;
        }
    }

</style>
  