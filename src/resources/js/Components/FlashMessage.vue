<script setup>
</script>

<template>
    <div v-if="$page.props.flash.status === 'success'" class="bg-blue-500 text-white p-4">
        {{ $page.props.flash.message }}
    </div>
    <div v-if="$page.props.flash.status === 'danger'" class="bg-red-300 text-white p-4 mb-4">
        {{ $page.props.flash.message }}
    </div>
</template>
