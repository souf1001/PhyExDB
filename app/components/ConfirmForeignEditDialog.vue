<script lang="ts" setup>
const { header, message, onEdit } = defineProps({
  header: {
    type: String,
    default: "Sind sie sich sicher?",
    required: false,
  },
  message: {
    type: String,
    default: "Das ist nicht ihr Experiment. Wollen sie es wirklich bearbeiten?",
    required: false,
  },
  onEdit: {
    type: Function,
    required: true,
  },
})
const visible = defineModel<boolean>()
</script>

<template>
  <AlertDialog :open="visible">
    <AlertDialogContent class="max-h-full overflow-auto">
      <AlertDialogHeader>
        <AlertDialogTitle>{{ header }}</AlertDialogTitle>
        <AlertDialogDescription>
          {{ message }}
        </AlertDialogDescription>
      </AlertDialogHeader>
      <AlertDialogFooter>
        <AlertDialogCancel @click="visible = false">
          Abbrechen
        </AlertDialogCancel>
        <AlertDialogAction
          class="hover:bg-destructive hover:text-destructive-foreground"
          @click="visible = false; onEdit()"
        >
          Bearbeiten
        </AlertDialogAction>
      </AlertDialogFooter>
    </AlertDialogContent>
  </AlertDialog>
</template>

<style>

</style>
