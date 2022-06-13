<template>
    <PureTaskList :tasks="tasks" @pin-task="pinTask" @archive-task="archiveTask"/>
</template>

<script>
import PureTaskList from './PureTaskList'
import { computed } from 'vue'
import { useStore } from 'vuex'

export default {
    name: 'TaskList',
    components: { PureTaskList },
    setup() {
        const store = useStore();
        const tasks = computed(() => store.state.tasks);
        const archiveTask = task => store.dispatch('archiveTask', task);
        const pinTask = task => store.dispatch('pinTask', task);

        return {
            tasks,
            archiveTask,
            pinTask
        }
    }
}
</script>