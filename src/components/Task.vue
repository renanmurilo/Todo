<template>
  <div @click="$emit('taskStateChanged', task)" class="task" :class="stateClass">
     <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
      <p class="conteudo"> {{ task.name }} </p>
  </div>
</template>

<script>
   export default {
      props: {
         task: { type: Object, required: true }
      },
      computed: {
         stateClass() {
            return {
               pending: this.task.pending,
               done: !this.task.pending
            }
         }
      }
   }
</script>

<style>
   .task {
      box-sizing: border-box;
      width: 340px;
      min-height: 150px;
      padding: 10px;
      border-radius: 18px;
      font-size: 2rem;
      font-weight: 300;
      cursor: pointer;
      user-select: none;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
   }

   .task .conteudo {
      max-width: 320px;
      word-break: break-word;
   }

   .pending {
      border-left: 12px solid #B73229;
      background-color: #f44336;
   }

   .done {
      color: #ddd;
      border-left: 12px solid #0A8F08;
      background-color: #4caf50;
      text-decoration: line-through;
   }

   .pending .close {
      background-color: #B73229;
   }

   .done .close {
      background-color: #0A8F08;
   }

   .close {
      position: absolute;
      top: 10px;
      right: 10px;
      font-size: 0.9rem;
      font-weight: 600;
      height: 20px;
      width: 20px;
      border-radius: 10px;
      display: flex;
      justify-content: center;
   }
</style>