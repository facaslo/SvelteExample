<script>
	import Book from './book.svelte'	
	import Button from './button.svelte'
	let title = '';
	let price = 0;
	let description = '';
	let books =[];
	function setTitle(event){
		title = event.target.value;
	}
	function addBook(){		
		const newBook = {
				title : title,
				price : price,
				description: description
		};
		books = books.concat(newBook)
  }
</script>
<!-- ********************************************* -->
<style>
	h1 {
		color: purple;
		text-align: center;
		font-size: 2rem;
	}
	hr {
		color: purple;
	}
	section{
		margin: auto;
		width :30rem;

	}
	label,input,textarea{width: 100%}
</style>
<!-- ********************************************* -->
<section>
	<h1> Book Store </h1>
	<hr/>
</section>
<section>
	<h2> Add new book </h2>
	<div> 
		<label for="title">Title</label>
		<input type="text" id="title" value={title} on:input={setTitle}/>
	</div>
	<div>
		<label for="price">Price</label>
		<input type="number" id="price" bind:value={price}/>
	</div>
	<div>
		<label for="description">Description</label>
		<textarea rows="3" id="description" bind:value ={description}/>
	</div>
	<div>
		<Button on:click={addBook}>ADD Book</Button>
	</div>
	<hr/>
</section>
<section>
	{#if books.length === 0}
			<p>
				No books in stock. 
			</p>
	{:else}
			{#each books as book}
					<Book bookTitle={book.title} bookPrice={book.price} bookDescription={book.description}/>
			{/each}
	{/if}
</section>