<script lang="ts" setup>
import { onUpdated, ref } from 'vue'
import { Colors } from '../color';
import Button from './Button.vue'

let input = "";
const activeList = ref([]);
const doneList = ref([]);

const onChangeInput = (e) => input = e.target.value;

const addItem = () => {
    if (input) {
        activeList.value.push(input);
    }
};

const deleteItem = (index) => {
    doneList.value.splice(index, 1);
};

const convertItem = (currentIndex, convertType) => {
    switch (convertType) {
        case "toActive":
            activeList.value.push(doneList.value[currentIndex]);
            doneList.value.splice(currentIndex, 1);
            break;
        case "toDone":
            doneList.value.push(activeList.value[currentIndex]);
            activeList.value.splice(currentIndex, 1);
            break;
    }
};

onUpdated(() => {
    input = "";
});
</script>

<template>
    <div class="container">
        <div class="input-area">
            <input :value="input" @change="onChangeInput" type="text" />
            <Button
                @emitted-click="addItem"
                text="Add"
                :font-color="Colors.white"
                :bg-color="Colors.primary.main"
            />
        </div>
        <div v-if="activeList.length" class="list">
            <div class="item" v-for="item, index in activeList">
                <p>{{ item }}</p>
                <Button
                    @emitted-click="convertItem(index, 'toDone')"
                    text="Done"
                    :font-color="Colors.primary.main"
                    :bg-color="Colors.white"
                />
            </div>
        </div>
        <p class="no-item-text" v-else>No Item 🥳</p>
        <details v-if="doneList.length">
            <summary>Done</summary>
            <div class="list">
                <div class="item done" v-for="item, index in doneList">
                    <p>{{ item }}</p>
                    <div class="btn-container">
                        <Button
                            @emitted-click="convertItem(index, 'toActive')"
                            text="Reopen"
                            :font-color="Colors.secondary.main"
                            :bg-color="Colors.white"
                        />
                        <Button
                            @emitted-click="deleteItem(index)"
                            text="Delete"
                            :font-color="Colors.white"
                            :bg-color="Colors.secondary.main"
                        />
                    </div>
                </div>
            </div>
        </details>
    </div>
</template>

<style scoped>
p {
    margin: 0;
}

.container {
    padding: 0 16px;
    max-width: 540px;
    margin: 0 auto;
}

.input-area {
    position: sticky;
    top: 64px;
    display: flex;
    column-gap: 8px;
}

.input-area input {
    width: 100%;
    border: 1px solid lightgray;
    border-radius: 4px;
    padding: 4px 8px;
    box-sizing: border-box;
    height: 36px;
}

.no-item-text {
    color: grey;
    margin-top: 40px;
    text-align: center;
}

.list {
    display: grid;
    gap: 8px;
    padding: 32px 0;
}

.item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 8px;
    background-color: #42b983;
    color: #ffffff;
    border-radius: 8px;
}

.item.done {
    background-color: #bc8f8f40;
}

.item.done p {
    color: grey;
    text-decoration: line-through;
}
.btn-container {
    display: flex;
    gap: 8px;
}

details {
    margin-top: 32px;
}
</style>
