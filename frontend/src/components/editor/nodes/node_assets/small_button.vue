<script setup>
import { ref, defineProps, computed } from 'vue';

const props = defineProps({
    component_stroke_color:String,
    component_bg_color:String,
    button_text:String,
    style_selection:0,
})
</script>
<template>
<button class="small_button_s1">{{ button_text }}</button>
</template>
<style scoped>
    .small_button{
        height:20px;
        width:20px;
        color: v-bind('component_stroke_color');
        font-weight: 800;
        border:v-bind('component_stroke_color') solid 1px;
        border-radius: 3px;
        background:white;
        margin-top:10px;
    }
    .small_button:hover{
        background-image: linear-gradient(180deg,white,white,v-bind(component_stroke_color));
    }
    .small_button_s1{
        height:20px;
        width:20px;
        color: white;
        font-weight: 800;
        border:v-bind('component_stroke_color') solid 1px;
        border-top:none;
        border-radius: 3px;
        background-image:linear-gradient(180deg,v-bind(component_bg_color),v-bind(component_stroke_color));
    }
    .small_button_s1:hover{
        background-image: linear-gradient(180deg,v-bind(component_bg_color), v-bind(component_bg_color),v-bind(component_stroke_color));
    }
</style>