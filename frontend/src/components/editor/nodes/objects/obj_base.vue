<script setup>
import { defineProps, watch, computed, ref } from 'vue';
import { useNodesStore } from '../node_store.js'
import NodeBase from '../node_base.vue'
import { DebugInfo } from '../node_assets/n-component-imports';

const props = defineProps({
  id: { default:-1},
  object_name: { type: String, default: 'UnnamedType' },
  stroke_color: { type: String, default: 'black' },
  bg_color: { type: String, default: 'white' },
  node_properties: { type: Array, default: () => [] },

});

const nodesStore = useNodesStore();
const node = computed(() => nodesStore.getNode(Number(props.id)));//the node in question is always the one with the same id as the props.id
const debug_message = "ID:"+props.id;   //whats displayed in the innermost part of the object on canvas
</script>

<template>  
<NodeBase :stroke_color="stroke_color"
          :bg_color="bg_color"
          :id="id">
<div class="object-name-container">{{ node.object_name }}</div>

<DebugInfo :info_text="debug_message"></DebugInfo>
</NodeBase>
</template>

<style scoped>
.object-name-container{
  font-size: 16px;
  background: v-bind('stroke_color');
  color:v-bind('bg_color');
  margin:0px !important;
  padding-left: 5px;
  padding-bottom: 2px;
  padding-right: 5px;
}
</style>