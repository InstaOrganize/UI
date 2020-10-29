<template>
  <div class="">
    <div class="pl-3 pt-3">
      <h2>Demo Board</h2>
      <hr />
    </div>
    <div class="row p-3">
      <div class="col-2">
        <h5>Todo</h5>
        <draggable
          class="list-group border p-1"
          :list="list1"
          group="people"
          @change="log"
        >
          <div
            class="list-group-item task"
            v-for="(element) in list1"
            :key="element.name">
            <div class="task-name col-12">{{ element.name }}</div>
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
            key="footer"
          >
          <button class="btn btn-secondary btn-sm float-right">
          <b-icon-plus></b-icon-plus>Add Task</button>
        </div>
        </draggable>
      </div>

      <div class="col-2">
        <h5>In Progress</h5>
        <draggable
          class="list-group border p-1"
          :list="list2"
          group="people"
          @change="log">
          <div
            class="list-group-item task align-items-start"
            v-for="(element) in list2"
            :key="element.name">
            <div class="task-name col-12">{{ element.name }}</div>
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
            key="footer"
          >
          <button class="btn btn-secondary btn-sm float-right">
          <b-icon-plus></b-icon-plus>Add Task</button>
        </div>
        </draggable>
      </div>
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
  list1 = [
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
  ];

  list2 = [
    {
      id: 7,
      name: 'Determine Requirements',
      comments: 5,
    },
    {
      id: 8,
      name: 'Meet With Stakeholders',
      comments: 3,
    },
    {
      id: 9,
      name: 'Lorem Ipsum',
      comments: 2,
    },
  ];

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
</style>
