<template>
    <div class="footer noselect" v-if="currentKeyspace">
        <div class="canvas-data">
            <div class="data-item"> entities: {{entities}}</div>
            <div class="data-item"> attributes: {{attributes}}</div>
            <div class="data-item"> relationships: {{relationships}}</div>
        </div>
    </div>
</template>

<style scoped>

    .footer {
        border-top: var(--container-darkest-border);
        background-color: #282828;
        padding: var(--container-padding);
        display: flex;
        flex-direction: row;
        z-index: 1;
        justify-content: flex-end;
    }

    .canvas-data {
        display: flex;
    }

    .data-item {
        justify-content: space-between;
        display: flex;
        margin-left: 5px;
    }

</style>

<script>

export default {
  name: 'Footer',
  props: ['localStore'],
  data() {
    return {
      entities: 0,
      attributes: 0,
      relationships: 0,
    };
  },
  computed: {
    currentKeyspace() {
      return this.localStore.getCurrentKeyspace();
    },
    getData() {
      return this.localStore.canvasData;
    },
  },
  watch: {
    getData(canvasData) {
      this.entities = canvasData.entities;
      this.attributes = canvasData.attributes;
      this.relationships = canvasData.relationships;
    },
  },
};
</script>
