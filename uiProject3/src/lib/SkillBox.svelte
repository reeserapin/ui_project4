<script>
    export let name;
    export let skillsHave = [];
    export let skillsLearn = [];
    export let imageUrl = ''; // Add a prop for the image URL
  
    let isRequestPending = false; // State to track the button status
  
    function handleRequestSwap() {
      isRequestPending = true; // Change the button text to "Pending"
    }
  </script>
  
  <div class="user-container">
    <div class="image-box">
      <img src={imageUrl} alt="{name}'s image" />
    </div>
    <div class="user-box">
      <h2>{name}</h2>
      <div class="skills">
        <p><strong>Skills I have:</strong></p>
        <ul>
          {#each skillsHave as skill}
            <li>{skill}</li>
          {/each}
        </ul>
      </div>
      <div class="skills">
        <p><strong>Skills I want to learn:</strong></p>
        <ul>
          {#each skillsLearn as skill}
            <li>{skill}</li>
          {/each}
        </ul>
      </div>
      <div class="request-container">
        <button class="request-button" on:click={handleRequestSwap} disabled={isRequestPending}>
          {isRequestPending ? "Pending" : "Request Swap"}
        </button>
      </div>
    </div>
  </div>
  
  <style>
    .user-container {
      display: flex;
      align-items: flex-start;
      border: 1px solid #ddd;
      border-radius: 8px;
      padding: 16px;
      margin: 8px;
      background-color: #f9f9f9;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      flex-wrap: wrap;
    }
  
    .image-box {
      margin-right: 16px;
    }
  
    .image-box img {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      object-fit: cover;
    }
  
    .user-box {
      flex: 1;
    }
  
    .skills {
      margin-top: 16px;
    }
  
    ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }
  
    .request-container {
      margin-top: 16px;
      text-align: center; /* Centers the button */
    }
  
    .request-button {
      background-color: #3fb5d2;
      color: white;
      border: none;
      border-radius: 4px;
      padding: 8px 16px;
      font-size: 1rem;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
  
    .request-button:hover {
      background-color: #3f5bbb;
    }
  
    .request-button:disabled {
      background-color: #ccc;
      cursor: not-allowed;
    }
  
    h2 {
      margin: 0;
      font-size: 1.5rem;
      color: #333;
    }
  </style>
  