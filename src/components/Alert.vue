<template>
    <div class="alert" v-if="show" :style="{ backgroundColor }">
        <div>{{ message }}</div>
        <div @click="$emit('close')" class="close-alert">&times;</div>
    </div>
</template>

<script>
export default {
    props:{
      message:{
        required: true,
        type: String,
      },
      show:{
        required: true,
        type: Boolean,
      },
      type:{
        default: "danger",
        validator(value){
          return ["danger","warning","info"].includes(value);
        }
      }
    },
    computed:{
      backgroundColor(){
        const options = {
          danger: 'var(--danger-color)',
          info: 'var(--info-color)',
          warning: 'var(--warning-color)'
        }

        return options[this.type]
      }
    },
    emits:['close'],
}
</script>

<style scoped>
.alert {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 50px;
  padding: 0 20px 0 20px;
  border-radius: 5px;
}

.close-alert {
  font-size: 50px;
  cursor: pointer;
}

</style>