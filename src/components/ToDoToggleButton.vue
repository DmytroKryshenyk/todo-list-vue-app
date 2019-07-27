<template>
  <div class="toggleButton">
    <label class="toggleButton__label">
      <span class="toggleButton__text">Move done items at the end?</span>
      <input class="toggleButton__input" type="checkbox" v-model="isSortButtonActive" @change="sortButtonChanged"/>
      <span class="toggleButton__box"></span>
    </label>
  </div>
</template>
<script>
export default {
  name: "ToDoToggleButton",
  data() {
    return {
      isSortButtonActive: false
    };
  },
  methods: {
    sortButtonChanged() {
      this.$emit('sortButtonChanged', this.isSortButtonActive)
    }
  }
};
</script>

<style lang="scss" scoped>
.toggleButton {
  margin-bottom: 2rem;
}

.toggleButton__label {
  display: block;
  position: relative;
  text-align: right;
}

.toggleButton__text {
  font-size: 0.8rem;
}

.toggleButton__input {
  position: absolute;
  opacity: 0;
  right: 0;
  top: 0;

  &:checked + .toggleButton__box::before {
    left: 100%;
    transform: translateX(-100%);
    opacity: 1;
  }
}

.toggleButton__box {
  display: inline-block;
  margin-left: 1rem;
  height: 1.2rem;
  width: 2rem;
  background: $actions-items-color;
  border-radius: 1.2rem;
  vertical-align: middle;
  position: relative;

  &::before {
    content: "";
    position: absolute;
    left: 0;
    height: 1.2rem;
    width: 1.2rem;
    border-radius: 1.2rem;
    border: 0.125rem solid $actions-items-color;
    box-sizing: border-box;
    background: $brand-color-2;
    opacity: 0.7;
    transition: left 0.2s ease-out, transform 0.2s ease-out,
      opacity 0.2s ease-out;
  }
}
</style>

