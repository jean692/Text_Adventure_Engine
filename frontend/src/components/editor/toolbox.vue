<script setup>

import useDragAndDrop from './drag_drop.js';
import node_colors from './nodes/node-colors.js'
import { TBNode } from './nodes/n-imports.js'
import { useProjectStore } from './project_store.js';


</script>
<template>
    <div class="toolbox">
        <a class="tb_title">Toolbox</a>
        <button class="tb_btn" @click="useProjectStore().initProject()">Init Project (temporary implementation)</button>
        <button class="tb_btn" @click="useProjectStore().renameProject()">Rename Project</button>
        <button class="tb_btn" @click="useProjectStore().exportProject()">Export Project</button>

        <a class="tb_subtitle">Objects</a>
                <TBNode node_type="room" display_type="Room" :bg_color="node_colors.room_bg" :stroke_color="node_colors.room_stroke"></TBNode>
                <TBNode node_type="item" display_type="Item" :bg_color="node_colors.item_bg " :stroke_color="node_colors.item_stroke"></TBNode>
                <TBNode node_type="npc" display_type="NPC" :bg_color="node_colors.npc_bg" :stroke_color="node_colors.npc_stroke"></TBNode>
                <TBNode node_type="pathway" display_type="Pathway" :bg_color="node_colors.pathway_bg" :stroke_color="node_colors.pathway_stroke"></TBNode>
                <TBNode node_type="custom" display_type="Custom" :bg_color="node_colors.custom_bg" :stroke_color="node_colors.custom_stroke"></TBNode>
        <a class="tb_subtitle">Interactive</a>
                <TBNode node_type="prompt" display_type="Prompt" :bg_color="node_colors.prompt_bg" :stroke_color="node_colors.prompt_stroke"></TBNode>
                <TBNode node_type="await" display_type="Await" :bg_color="node_colors.await_bg" :stroke_color="node_colors.await_stroke"></TBNode>
                <TBNode node_type="unimplemented" display_type="Action" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
                <TBNode node_type="unimplemented" display_type="OnPlayerEnter" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
                <TBNode node_type="unimplemented" display_type="OnPlayerNear" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
                <TBNode node_type="unimplemented" display_type="OnPlayerPossess" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
        <a class="tb_subtitle">Value</a>
                <TBNode node_type="unimplemented" display_type="ChangeProperty" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
                <TBNode node_type="unimplemented" display_type="ChangeLocation" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
                <TBNode node_type="unimplemented" display_type="Evaluate" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
        <a class="tb_subtitle">Path Control</a>
                <TBNode node_type="unimplemented" display_type="If" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
                <TBNode node_type="unimplemented" display_type="Switch" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
        <a class="tb_subtitle">Visual</a>
                <TBNode node_type="unimplemented" display_type="Time" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
                <TBNode node_type="unimplemented" display_type="Image" :bg_color="node_colors.unimplemented_bg" :stroke_color="node_colors.unimplemented_stroke"></TBNode>
    </div>
</template>

<style>
@import 'https://fonts.googleapis.com/css2?family=Syne+Mono&display=swap';

.toolbox{
    display:flex;
    flex-direction: column;
    width:auto;
    height:100%;
    background:rgb(209, 207, 216);
    border-right: 1px solid rgb(68, 46, 110);
    background-image: linear-gradient(180deg, rgb(197, 201, 179),rgb(214, 212, 199),rgb(214, 212, 199), rgb(214, 212, 199),rgb(215, 211, 185), rgb(191, 194, 179));
    overflow-y:scroll;
}

.toolbox>*{
    margin:6px;
}

.tb_title{

    font-family: 'Syne Mono', monospace;
    font-size: 22px;
    padding:8px;
    text-align: center;
    margin: 0 auto;
    margin-bottom:0px;

    width: 100%;
    height:min-content;
    color:rgb(78, 81, 76);
    background:rgb(189, 189, 189);
    background-image: linear-gradient(180deg, rgb(237, 248, 208),rgb(214, 212, 199),rgb(214, 212, 199), rgb(214, 212, 199),rgb(215, 211, 185), rgb(71, 70, 74));
    font-weight:500;
}

.tb_subtitle{
    font-family: 'Syne Mono', monospace;
    padding:4px;
    margin: 0 auto;
    margin-bottom:0px;

    width: 100%;
    height:min-content;
    color:rgb(78, 81, 76);
    font-weight:600;
    font-size:14px;
}


.context-menu {
    position: absolute;
    background: white;
    border: 1px solid #ccc;
    z-index: 1000;
    box-shadow: 0 2px 10px rgba(0,0,0,0.2);
}

.context-menu ul {
    list-style: none;
    margin: 0;
    padding: 0;
}

.context-menu li {
    padding: 10px;
    cursor: pointer;
}

.context-menu li:hover {
    background: #f0f0f0;
}
</style>
