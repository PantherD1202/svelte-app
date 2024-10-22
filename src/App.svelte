<script>
	import { onMount } from 'svelte';
	import './styles/styles.css'
  
	let products = [];
  
	onMount(async () => {
		try {
			const response = await fetch('http://127.0.0.1:8000/products/');
			if (response.ok) {
				products = await response.json();
			} else {
				console.error('Failed to fetch products:', response.statusText);
			}
		} catch (error) {
			console.error('Error fetching data:', error);
		}
	});
  </script>
  
  <main>
    <h1>Products List</h1>
    <table border="1" cellspacing="0" cellpadding="10">
        <thead>
            <tr>
                <th>Name</th>
                <th>Description</th>
                <th>Stock</th>
                <th>Price</th>
                <th>Category</th>
            </tr>
        </thead>
        <tbody>
            {#each products as product}
                <tr>
                    <td>{product.name}</td>
                    <td>{product.description}</td>
                    <td>{product.stock_quantity}</td>
                    <td>{product.price}</td>
                    <td>{product.category}</td>
                </tr>
            {/each}
        </tbody>
    </table>
</main>

  