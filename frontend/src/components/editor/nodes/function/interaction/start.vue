<script setup>
import { ref, defineProps, computed } from 'vue';
import NodeBase from '../../node_base.vue'
import { Handle, Position } from '@vue-flow/core';
import { SmallButton, HContainer, HandleIn, HandleOut, Textboxes, VContainer } from '../../node_assets/n-component-imports.js';
import node_colors from '../../node-colors';
import FunctionBase from '../func_base.vue'
let response_id = 0;
const props = defineProps({
    id: { default:-1},
})

//----------------------------!!IMPORTANT FOR NODE DATA MANIPULATION/FETCHING!!---------------------------------------------
// ADD TO BE ABLE TO STORE OR RETRIEVE DYNAMIC INFORMATION FROM THE NODE ITSELF
// Component MUST have props.id for this to work, and it needs to be passed down through each component
// Parent component must also have @init-node-id listener
import { useNodesStore } from '@/components/editor/nodes/node_store'
const NS = useNodesStore()
const defaultObjData =  { //This is the data that this component contributes. Any existing properties within the functional node data will be replaced
    display_type:"Start",
    function_name: "start"
  }
  console.log("start.vue: ReferenceID is = " + props.id)
  NS.contributeNodeData(props.id,defaultObjData);
//------------------------------IMPORTANT END-------------------------------------------
</script>


<template>



    <FunctionBase
        :id="id"
        >
        <HContainer outerMargin="0px">
            <VContainer>
            <div style="width:150px; color:purple;">Your adventure begins here!</div> <div style="width:150px; color:purple;">To direct the script, place down a node with an input (Try prompt!) and drag the Start node's output to the other node's input </div>
            </VContainer>
            <HandleOut :id="id"></HandleOut>
        </HContainer>
    </FunctionBase>



</template>


<style scoped>
    .console_response_text{
        resize:none;
        width:200px;
        height:100px;
        background:rgb(255, 255, 255);
        /* border:solid v-bind('node_colors.prompt_fg') 1px; */
        border-radius:3px;
    }
    .user_response_text{
        resize:none;
        width:200px;
        height:auto;
        color:black;
        background:rgb(255, 255, 255);
        /* border:solid v-bind('node_colors.prompt_fg') 1px; */
        border-radius:3px;
    }
    .user_response_container{
        /* color: v-bind('node_colors.prompt_fg'); */
        /* background:v-bind('node_colors.prompt_bg'); */
        margin: 0px;
        padding-left:10px;
        padding-bottom:5px;
    }
    .response_title{
        display:flex;
    }
</style>