<template>
    <div class="demo-container">
        <h2>2. v-show在template标签问题</h2>

        <div class="demo-row">
            <div class="demo-col error">
                <h3>🚫 错误用法 (template使用v-show)</h3>
                <button @click="toggleError">切换显示 (当前: {{ errorVisible ? '显示' : '隐藏' }})</button>

                <!-- 这个v-show实际上不会生效 -->
                <!-- eslint-disable-next-line -->
                <template v-show="errorVisible">
                    <div class="demo-item">内容区块1</div>
                    <div class="demo-item">内容区块2</div>
                </template>

                <p class="demo-hint">
                    问题：v-show在template上无效<br>
                    实际效果：内容始终不显示
                </p>
            </div>

            <div class="demo-col correct">
                <h3>✅ 正确做法 (使用实际元素包裹)</h3>
                <button @click="toggleCorrect">切换显示 (当前: {{ correctVisible ? '显示' : '隐藏' }})</button>

                <!-- 使用div包裹 -->
                <div v-show="correctVisible">
                    <div class="demo-item">内容区块1</div>
                    <div class="demo-item">内容区块2</div>
                </div>

                <p class="demo-hint">
                    解决：使用实际HTML元素应用v-show<br>
                    效果：能正常切换display样式
                </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            errorVisible: true,
            correctVisible: true
        }
    },
    methods: {
        toggleError() {
            this.errorVisible = !this.errorVisible
            console.log('错误用法切换:', this.errorVisible)
        },
        toggleCorrect() {
            this.correctVisible = !this.correctVisible
            console.log('正确用法切换:', this.correctVisible)
        }
    }
}
</script>

<style scoped>
/* 保持样式不变 */
.demo-item {
    padding: 12px;
    margin: 8px 0;
    background: #f8f8f8;
    border-radius: 4px;
    border-left: 4px solid #42b983;
}

.demo-container {
    max-width: 900px;
    margin: 0 auto;
    padding: 20px;
}

.demo-row {
    display: flex;
    gap: 30px;
    margin: 30px 0;
}

.demo-col {
    flex: 1;
    padding: 20px;
    border: 2px solid;
    border-radius: 8px;
}

.error {
    border-color: #ff6b6b;
}

.correct {
    border-color: #42b983;
}

.demo-hint {
    color: #666;
    font-size: 0.9em;
    margin-top: 15px;
}

button {
    padding: 8px 16px;
    background: #35495e;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-bottom: 15px;
}

button:hover {
    background: #42b983;
}

h2 {
    color: #2c3e50;
    border-bottom: 1px solid #eee;
    padding-bottom: 10px;
}

h3 {
    margin-top: 0;
    color: inherit;
}
</style>