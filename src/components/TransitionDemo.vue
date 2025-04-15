<template>
    <div class="transition-demo">
        <h2>Transition 动画完整实现</h2>

        <div class="demo-section">
            <div class="demo-col error">
                <h3>🚫 常见错误</h3>
                <button @click="showError = !showError">切换显示</button>

                <!-- 典型错误写法 -->
                <!-- 这里过渡不会生效 -->
                <div v-show="showError" 
                    class="box error-box" 
                    style="transition: all 0.5s">
                    内容区域
                </div>

                <p class="hint">
                    问题：元素直接出现/消失<br>
                    （CSS过渡被v-if的DOM操作覆盖）
                </p>
            </div>

            <div class="demo-col correct">
                <h3>✅ 正确实现</h3>
                <button @click="showCorrect = !showCorrect">切换显示</button>

                <!-- 正确实现方案 -->
                <transition name="fade">
                    <div v-show="showCorrect" class="box correct-box">
                        内容区域
                    </div>
                </transition>

                <p class="hint">
                    效果：完整0.5秒淡入淡出<br>
                    （包含透明度+位移动画）
                </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            showError: false,
            showCorrect: false
        }
    }
}
</script>

<style scoped>
.transition-demo {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    font-family: Arial, sans-serif;
}

.demo-section {
    display: flex;
    gap: 30px;
    margin-top: 30px;
}

.demo-col {
    flex: 1;
    padding: 20px;
    border-radius: 8px;
}

.error {
    border: 2px solid #ff6b6b;
    background: #fff5f5;
}

.correct {
    border: 2px solid #42b983;
    background: #f5fff7;
}

button {
    padding: 8px 16px;
    background: #35495e;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-bottom: 15px;
    font-size: 14px;
}

.hint {
    color: #555;
    font-size: 0.9em;
    margin-top: 15px;
    padding: 10px;
    background: white;
    border-radius: 4px;
    line-height: 1.5;
}

.box {
    padding: 30px;
    margin: 15px 0;
    text-align: center;
}

.error-box {
    background: #ffebee;
    border-left: 4px solid #ff6b6b;
}

.correct-box {
    background: #e8f5e9;
    border-left: 4px solid #42b983;
}

.fade-enter-active {
    transition: all 0.5s ease-out;
    /* 入场动画 */
}

.fade-leave-active {
    transition: all 0.5s ease-in;
    /* 离场动画 */
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateY(20px);
    /* 入场起始状态和离场结束状态 */
}
</style>