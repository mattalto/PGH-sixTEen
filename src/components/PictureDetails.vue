<template>
    <div v-if="isOpen" class="modal-backdrop">
        <div class="modal-wrapper">
            <div class="modal-container" ref="target">
                <div class="modal-details">
                    <!-- here is where we would render the prop passed from the parent component
                        to display the correct description based on which picture is clicked 
                    <slot name="details">{{ pictureDescription }}</slot> -->
                    <div>
                        <p @click.stop="$emit('modal-close')">{{ pictureDescription }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
    import { defineProps, defineEmits, ref } from 'vue';
    import { onClickOutside } from '@vueuse/core'
    // This function detects clicks outside of the modal to then close the modal.
    // Better UX

    const props = defineProps({
        isOpen: Boolean,
        pictureDescription: String,
        pictures: Array
    });

    const emit = defineEmits(["modal-close"]);
    // Emitting modal-close event allows the parent component to handle the closure instead

    const target = ref(null)
    onClickOutside(target, () => emit('modal-close'))
</script>

<style scoped>
    .modal-backdrop {
        position: fixed;
        z-index: 999;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
    }

    .modal-container {
        width: 300px;
        margin: 150px auto;
        padding: 20px 30px;
        background-color: #fff;
        border-radius: 2rem;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
    }

    .modal-details p {
        color: black;
    }
</style>