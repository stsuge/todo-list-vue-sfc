<template>
    <!-- 絞り込みラジオボタン -->
    <label v-for="option in options">
        <input type="radio" v-model="current" v-bind:value="option.value">{{ option.label }}
    </label>
</template>

<script>
export default {
    data() {
        return {
            // 状態での絞り込みの選択肢
            options: [
                { value: -1, label: 'すべて' },
                { value: 0, label: '作業中' },
                { value: 1, label: '完了' }
            ],
            // 選択している options の value を記憶するためのデータ
            // 初期値を「-1」つまり「すべて」にする
            current: -1,
        }
    }

}
</script>