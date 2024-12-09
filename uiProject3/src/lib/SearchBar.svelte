<script>
    import { createEventDispatcher } from "svelte";
  
    const dispatch = createEventDispatcher();
    let searchTerm = "";
  
    function handleInput(event) {
      searchTerm = event.target.value;
      dispatch("search", searchTerm); // Emit the search term to the parent
    }
  </script>
  
  <div class="search-bar">
    <input
      type="text"
      placeholder="Search by skill..."
      on:input={handleInput}
      bind:value={searchTerm}
    />
  </div>
  
  <style>
    .search-bar {
      position: fixed;
      padding: 20px;
    }
    input {
      width: 80%;
      padding: 8px;
      font-size: 1rem;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    input:focus {
      outline: none;
      border-color: #0077cc;
      box-shadow: 0 0 5px rgba(0, 119, 204, 0.5);
    }
  </style>
  