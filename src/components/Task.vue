<template>
    <div 
    @click="$emit('taskStateChanged', task)"
    class="task" :class="stateClass">
        <span @click="$emit('taskDeleted', task)" class="close">X</span>
<p>{{ task.name }}</p>
    </div>
</template>

<script> 
export default {
props: {
    task: { type: Object, required: true}
},
computed: { 
    stateClass() { // verifica se a atividade está pendente ou não.
        return {
            pending: this.task.pending, // se a tarefa está pendente 
            done: !this.task.pending, // se a tarefa estiver concluída.
        }
    }
}
}
</script>

<style>
.task {
    position: relative;
    box-sizing: border-box; 
    width: 350px; 
    max-width: 100%;
    height: 150px;
    max-height: 100%;
    padding: 10px;
    border-radius: 8px; 
    font-size: 2rem; 
    font-weight: 300;
    cursor: pointer; /* o cursor muda ao passar nas letras  */
    user-select: none; /* usuário n consegue selecionar o texto */
    display: flex;
    justify-content: center; 
    align-items: center;
}
/* Cor para o  Status pendente  */
.pending {
    border-left: 12px solid #B73229;
    background-color: #F44336;
}
/* Cor para o  Status concluída  */
.done {
    color: #DDD;
    border-left: 12px solid #0A8F08;
    background-color: #4CAF50;
    text-decoration: line-through;
}

.pending .close {
    background-color: #B73229;
}
.pending .done {
    background-color: #0A8F08;
}

.close { 
    position: absolute;
    right: 10px;
    top: 10px;
    font-size:  0.9rem;
    font-weight: 600; 
    height: 20px; 
    width: 20px;
    border-radius: 10px;
    display: flex;
    justify-content: center;
}

</style>