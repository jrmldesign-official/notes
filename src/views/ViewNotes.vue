<template>
<div class="notes">

	<div class="card has-background-success-dark p-4 mb-5">
		<div class="field">
			<div class="control">
				<textarea ref="newNoteRef" v-model="newNote" class="textarea" placeholder="Add a new note" />
			</div>
		</div>

		<div class="field is-grouped is-grouped-right">
			<div class="control">
				<button @click="addNote" :disabled="!newNote" class="button is-link has-background-success">Add New Note +</button>
			</div>
		</div>
	</div>

	<div
		v-for="note in notes"
		:key="note.id"
	 	class="card"
	>
		<div class="card-content">
			<div class="content">
				{{ note.content }}
			</div>
		</div>
		<footer class="card-footer">
			<a href="#" class="card-footer-item">Edit</a>
			<a href="#" class="card-footer-item">Delete</a>
		</footer>
	</div>
</div>
</template>

<script setup>
// IMPORTS
import { ref } from 'vue'
import { v4 as uuidv4 } from 'uuid';

const newNote = ref('')
const newNoteRef = ref(null)

const notes = ref([
	{
		id: 1,
		content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestiae tempore reiciendis sit deserunt nostrum reprehenderit est. Cumque porro dolores, quidem unde ratione eligendi nesciunt! Iusto veritatis consectetur quis modi magnam!',
	},
	{
		id: 2,
		content: 'This is a shorter note! Wooo!'
	},
])

const addNote = () => {
	let note = {
		id: uuidv4(),
		content: newNote.value
	}

	notes.value.unshift(note)
	newNote.value = ''

	newNoteRef.value.focus()
}
</script>