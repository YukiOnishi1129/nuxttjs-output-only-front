<script setup lang="ts">
type Props = {
  disabled?: boolean;
  modelValue?: string;
  name: string;
  placeholder?: string;
  onKeydown?: (event: KeyboardEvent) => void;
};

type Emits = {
  (e: "update:modelValue", value: string): void;
};

const { disabled, modelValue, name, placeholder, onKeydown } =
  defineProps<Props>();

defineEmits<Emits>();
</script>

<template>
  <input
    type="text"
    class="input"
    :disabled="disabled"
    :name="name"
    :placeholder="placeholder"
    :value="modelValue"
    @input="
      $emit('update:modelValue', ($event.target as HTMLInputElement).value)
    "
    @keydown="onKeydown"
  />
</template>

<style scoped>
.input {
  color: #fff;
  border: none;
  background: rgba(0, 0, 0, 0.2);
  width: 100%;
  height: 50px;
  padding: 10px;
  box-sizing: border-box;
  font-size: 20px;
  font-family: "Times New Roman", Times, serif;
  border-radius: 5px;
}

.input:disabled {
  color: #c0c0c0;
}

.input::placeholder {
  color: #c0c0c0;
}
</style>
