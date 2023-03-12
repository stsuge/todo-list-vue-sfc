<template>
    {{ computedTodos.length }} 件を表示中
    <table>
        <thead>
            <tr>
                <th class="id">ID</th>
                <th class="comment">コメント</th>
                <th class="state">状態</th>
                <th class="button">-</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in computedTodos" v-bind:key="item.id">
                <td>{{ item.id }}</td>
                <td>{{ item.comment }}</td>
                <td class="state">
                    <button v-on:click="doChangeState(item)">{{ labels[item.state] }}</button>
                </td>
                <td class="button">
                    <button v-on:click="doRemove(item)">削除</button>
                </td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    props: {
        current: { type: Number, require: true, default: -1 },
    },
    data() {
        return {
            todos: []
        }
    },
    computed: {
        computedTodos: function () {
            // データ current が -1 ならすべて
            // それ以外なら current と state が一致するものだけに絞り込む
            return this.todos.filter(function (el) {
                return this.current < 0 ? true : this.current === el.state
            }, this)
        }
    },
    method: {
        // 状態変更の処理
        doChangeState: function (item) {
            item.state = item.state ? 0 : 1
        },
        // 削除の処理
        doRemove: function (item) {
            var index = this.todos.indexOf(item)
            this.todos.splice(index, 1)
        }
    }
}
</script>
