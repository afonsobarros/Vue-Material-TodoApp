<template>
  <div>
    <header>
      <md-field>
        <label>Add new task</label>
        <md-input v-model="newtask"></md-input>
      </md-field>
      <md-button class="md-raised md-primary" :disabled="!newtask" @click="addTask">add</md-button>
    </header>
    <md-card v-if="tasks.length > 0">
    <md-list class="md-triple-line" >
      <div v-for="(task,index) in tasks" :key="index">
        <md-divider v-if="index != 0"></md-divider>
        <md-list-item>
          <md-switch class="md-primary" v-model="task.done">
            <span :class="{ done: task.done }">
              {{task.text}}</span></md-switch>
          <md-button class="md-icon-button md-list-action" @click="removeTask(task)" matTooltip="Delete task">
            <md-tooltip md-direction="top">Delete task</md-tooltip>
            <md-icon>delete</md-icon>
          </md-button>
        </md-list-item>
      </div>
    </md-list>
    </md-card>
  </div>
</template>

<script>
export default {
  name: "TodoComponent",
  data() {
    return {
      newtask: null,
      tasks: []
    };
  },
  methods: {
    addTask() {
      this.tasks.push({
        text: this.newtask,
        done: false
      });
      this.newtask = null;
    },
    removeTask(task) {
      this.tasks.splice(this.tasks.indexOf(task), 1);
    },
    toggle(task) {
      task.done = !task.done;
    }
  }
};
</script>

<style>
.done {
  text-decoration: line-through;
  opacity: 0.5;
}
header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
.md-list.md-triple-line .md-list-item-content {
  min-height: auto;
}
.md-field {
  margin: 4px 0;
}
</style>
