<script>
	import FeedbackForm from './components/FeedbackForm.svelte'
	import FeedbackList from './components/FeedbackList.svelte'
	import FeedbackStats from './components/FeedbackStats.svelte'
$: feedback = [
	{
		id: 1, 
		rating: 10, 
		text: 'Sint ipsum dolor eiusmod elit. Lorem non qui cillum deserunt culpa magna. Veniam et exercitation qui non enim reprehenderit consectetur veniam quis sunt ad minim ad aute. Qui qui est nisi officia laborum do do voluptate excepteur dolor amet proident. Esse amet ipsum pariatur ullamco fugiat est anim minim. Commodo cillum mollit elit consequat et voluptate est.',
	},
	
	{
		id: 2, 
		rating: 5, 
		text: 'Sint ipsum dolor eiusmod elit. Lorem non qui cillum deserunt culpa magna. Veniam et exercitation qui non enim reprehenderit consectetur veniam quis sunt ad minim ad aute. Qui qui est nisi officia laborum do do voluptate excepteur dolor amet proident. Esse amet ipsum pariatur ullamco fugiat est anim minim. Commodo cillum mollit elit consequat et voluptate est.',
	},
	
	{
		id: 3, 
		rating: 7, 
		text: 'Sint ipsum dolor eiusmod elit. Lorem non qui cillum deserunt culpa magna. Veniam et exercitation qui non enim reprehenderit consectetur veniam quis sunt ad minim ad aute. Qui qui est nisi officia laborum do do voluptate excepteur dolor amet proident. Esse amet ipsum pariatur ullamco fugiat est anim minim. Commodo cillum mollit elit consequat et voluptate est.',
	}
]

$: count = feedback.length
$: average = feedback.reduce((a, {rating}) => a + rating, 0) / feedback.length

const addFeedback = (e) => {
	const newFeedback = e.detail 
	feedback = [newFeedback, ...feedback]
}
const deleteFeedback = (e) => {
	const itemId = e.detail
	feedback = feedback.filter((item) => item.id != itemId)
}
</script>

<main class="container">
	<FeedbackForm on:add-feedback={addFeedback}/>
	<FeedbackStats {count} {average} />
	<FeedbackList {feedback} on:delete-feedback={deleteFeedback}/>
</main>

<style>

</style>