<script setup lang="ts">
import { ref } from 'vue'

const count = ref<number>(0)
const font = ref<string>("Reggae One")

function update() {
    const canvas = document.getElementById('canvas') as HTMLCanvasElement;
    const ctx = canvas?.getContext('2d');
    if (!ctx) return;
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.font = '128px ' + font.value;

    const textarea = document.getElementById('text') as HTMLTextAreaElement;
    var lines = textarea.value.split('\n');

    for (var i = 0; i<lines.length; i++) {
        var line = lines[i] as string;

        let metrics = ctx.measureText(line);
        var x = (128 - metrics.actualBoundingBoxRight + metrics.actualBoundingBoxLeft) / 2;
        var y = (128 - metrics.actualBoundingBoxDescent + metrics.actualBoundingBoxAscent) / 2;

        console.log(x, y);

        var lineheight = 128;

        ctx.fillText(lines[i], x, y + (i * lineheight) );
    }
}
</script>

<template>
    <h1>Slack Emoji</h1>
    <button v-if="font !== 'Reggae One'" @click="font = 'Reggae One' ; update()">Reggae One</button>
    <button v-if="font !== 'Yusei Magic'" @click="font = 'Yusei Magic' ; update()">Yusei Magic</button>
    <button v-if="font !== 'Zen Maru Gothic'" @click="font = 'Zen Maru Gothic' ; update()">Zen Maru Gothic</button>
    <div class="card">
        <textarea id="text" @input="update"></textarea>
    </div>
    <div class="card">
        <canvas id="canvas" width="128" height="128"></canvas>
    </div>
    <div class="card">
        <p>Count: {{ count }}</p>
    </div>
</template>

<style lang="css" scoped>
@import url('https://fonts.googleapis.com/css2?family=Reggae+One&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Reggae+One&family=Yusei+Magic&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Reggae+One&family=Yusei+Magic&family=Zen+Maru+Gothic&display=swap');
canvas {
    border: 1px solid black;
}
</style>