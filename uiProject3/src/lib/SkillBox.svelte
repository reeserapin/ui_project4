<script>
    export let name;
    export let skillsHave = [];
    export let skillsLearn = [];
    export let imageUrl = ''; // Add a prop for the image URL
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
    }
  
    .image-box {
      margin-right: 16px;
    }
  
    .image-box img {
      width: 100px; /* Adjust the width as needed */
      height: 100px; /* Maintain aspect ratio or adjust as needed */
      border-radius: 50%; /* Makes the image circular */
      object-fit: cover;
    }
  
    .user-box {
      flex: 1;
    }
  
    .skills {
      margin-top: 8px;
    }
  
    ul {
      padding-left: 16px;
    }
  </style>
  