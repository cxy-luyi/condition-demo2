<template>
    <div id="app">
        <h2>Vue v-if/v-show Key Pitfall Demo</h2>
        <button @click="toggleShow">
            {{ show ? 'Hide Counter' : 'Show Counter' }}
        </button>
        <div class="switch">
            <label>
                <input type="radio" v-model="useVif" :value="true" name="mode" />
                Use v-if
            </label>
            <label>
                <input type="radio" v-model="useVif" :value="false" name="mode" />
                Use v-show
            </label>
        </div>
        <div class="key-control">
            <label>
                <input type="checkbox" v-model="useKey" />
                Use Dynamic Key
            </label>
        </div>

        <!-- 动态切换 v-if/v-show -->
        <Counter v-if="useVif && show" :key="useKey ? uniqueKey : 0" />
        <Counter v-show="!useVif && show" :key="useKey ? uniqueKey : 0" />
    </div>
</template>

<script setup>
import { ref } from 'vue'
import Counter from './CounterComponent.vue'

const show = ref(true)
const useVif = ref(true) // 初始为 v-if
const useKey = ref(false)
const uniqueKey = ref(0)

const toggleShow = () => {
    show.value = !show.value
    if (useKey.value) {
        uniqueKey.value = Math.random()
    }
}
</script>