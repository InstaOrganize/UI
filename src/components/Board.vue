<template>
  <div class="board">
    <div class="pl-3 pt-3 board-title">
      <h2>{{ boardTitle }}</h2>
      <hr />
    </div>
    <div class="container-fluid horizontal-scrollable">
        <draggable
            :list="groups"
            class="row p-3 flex-nowrap"
            group="groups">
          <div class="col-12 col-md-6 col-lg-3 col-xl-2" v-for="(group) in groups" :key="group.id">
            <h5 class="group-title bg-primary text-light p-2">{{group.title}}</h5>
            <draggable
              class="list-group border p-1"
              :list="group.tasks"
              group="tasks"
              @change="log">
              <div
                class="list-group-item task"
                v-for="(element) in group.tasks"
                :key="element.id">
                <!-- <div class="task-name col-12">{{ element.name }}</div> -->
                <div class="task-name col-12"><input type="input" v-model="element.name"
                  class="form-control task-input" /></div>
                <div class="task-name col-12"><span>
                  {{ element.comments }} <b-icon-chat-right-text></b-icon-chat-right-text>
                </span>
                <span class="ml-2" v-if="element.description">
                <b-icon-justify-left></b-icon-justify-left></span></div>
              </div>
              <div
                slot="footer"
                class="btn-group list-group-item"
                role="group"
                aria-label="Basic example"
                key="footer">
              <button v-on:click="newTask(group)" class="btn btn-outline-success
              btn-sm btn-rounded float-right">
              <b-icon-plus></b-icon-plus>New Task</button>
            </div>
            </draggable>
          </div>
        </draggable>
      </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import draggable from 'vuedraggable';

@Component({
  components: {
    draggable,
  },
})
export default class Board extends Vue {
  groups = [
    {
      id: '1',
      title: 'Todo',
      tasks: [
        {
          id: 4,
          name: 'Design Web Page',
          comments: 3,
          description: false,
        },
        {
          id: 5,
          name: 'Start Coding',
          comments: 0,
          description: true,
        },
        {
          id: 6,
          name: 'New Design Work',
          comments: 1,
          description: true,
        },
      ],
    },
    {
      id: '2',
      title: 'In Progress',
      tasks: [
        {
          id: 1,
          name: 'Design Web Page',
          comments: 3,
          description: false,
        },
        {
          id: 2,
          name: 'Start Coding',
          comments: 0,
          description: true,
        },
        {
          id: 3,
          name: 'New Design Work',
          comments: 1,
          description: true,
        },
      ],
    },
    {
      id: '2',
      title: 'In Progress',
      tasks: [
        {
          id: 3444,
          name: 'Design Web Page',
          comments: 3,
          description: false,
        },
        {
          id: 345,
          name: 'Start Coding',
          comments: 0,
          description: true,
        },
        {
          id: 543,
          name: 'New Design Work',
          comments: 1,
          description: true,
        },
      ],
    },
    {
      id: '2',
      title: 'In Progress',
      tasks: [
        {
          id: 143,
          name: 'Design Web Page',
          comments: 3,
          description: false,
        },
        {
          id: 662,
          name: 'Start Coding',
          comments: 0,
          description: true,
        },
        {
          id: 3556,
          name: 'New Design Work',
          comments: 1,
          description: true,
        },
      ],
    },
  ];

  boardTitle = 'Demo Board';

  newTask = (taskGroup: any) => {
    const newTaskId = Math.random();
    taskGroup.tasks.push({ id: newTaskId, name: `New Task: ${newTaskId}`, comments: 0 });
  };

  log = () => {
    console.log('Moved');
  };
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 .task{
   cursor: grab;
 }
 .task-name {
    font-size: 12px;
 }
 .task-input {
    padding: 0px;
    font-size: 12px;
    border: 0px;
    cursor: pointer;
 }
 .task-input:focus {
    padding: 0px;
    font-size: 12px;
    border: 0px;
    border-color: #000;
    cursor:text;
 }
</style>
