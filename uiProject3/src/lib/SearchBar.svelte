<script>
    import { createEventDispatcher } from "svelte";
  
    const dispatch = createEventDispatcher();
    let searchTerm = "";
    let isFilterActive = false; // State to track filter button status
  
    function handleInput(event) {
      searchTerm = event.target.value;
      dispatch("search", searchTerm); // Emit the search term to the parent
    }
  
    function toggleFilter() {
      isFilterActive = !isFilterActive;
      dispatch("filter", isFilterActive); // Emit the filter status to the parent
    }
  </script>
  
  <div class="search-bar">
    <input
      type="text"
      placeholder="Search by skill..."
      on:input={handleInput}
      bind:value={searchTerm}
    />
    <button class="filter-button" on:click={toggleFilter}>
      {isFilterActive ? "Filter: ON" : "Filter: OFF"}
    </button>
  </div>
  
  <style>
    .search-bar {
      display: flex;
      align-items: center;
      gap: 8px; /* Space between input and button */
      padding: 20px;
    }
  
    input {
      flex: 1; /* Make input take up the remaining space */
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
  
    .filter-button {
      background-color: #5271ff;
      color: white;
      border: none;
      border-radius: 4px;
      padding: 8px 16px;
      font-size: 1rem;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
  
    .filter-button:hover {
      background-color: #3f5bbb;
    }
  
    .filter-button:active {
      background-color: #2c3d7d;
    }
  </style>
  