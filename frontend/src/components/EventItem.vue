<template>
  <div class="item">
    <div class="details">
      <div class="name">Name: {{ props.item!.name }}</div>
      <div class="date">Date: {{ props.item!.date }}</div>
    </div>
    <div class="delete-button" v-on:click="deleteEvent()">
      <img alt="delete-icon" class="delete-icon" src="@/assets/delete.svg" width="24" height="24" />
    </div>
  </div>
</template>

<script setup lang="ts">
import AlertHelper from "@/helpers/AlertHelper";
import EventModel from "@/types/EventModel";

const props = defineProps({
  item: EventModel
})

function deleteEvent() {
  AlertHelper.confirmDialog({question:"Are you sure you want to delete this event?"}).then(confirmed=>console.log(confirmed))
}

</script>

<style scoped>

.item{
  margin: 12px;
  padding: 12px;
  background-color: white;
  border-radius: 12px;
  box-shadow: 1px 1px #dadada;
  display: flex;
}

.details{
  flex: 1;
}

.name{
  font-weight: bold;
}

.delete-button{
  background-color: red;
  padding: 12px;
  border-radius: 12px;
}

.delete-button:hover{
  transition: 100ms;
  transform: scale(1.02);
}

.delete-button:active {
  transform: scale(0.9);
  box-shadow: 0 0 0 0 #fff;
}

.delete-icon{
  display: block;
  filter: invert(96%) sepia(6%) saturate(241%) hue-rotate(227deg) brightness(117%) contrast(100%);
}



</style>