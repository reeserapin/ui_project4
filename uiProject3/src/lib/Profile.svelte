<script>
    let pfpUrl = "./CSGIRLY.webp"; // Placeholder image
    let name = "/cynthiasmith.png";
    let username = "cynthia_smith"; // New username variable
    let skillsHave = ["HTML", "CSS"];
    let skillsLearn = ["JavaScript", "Svelte"];
    
    // State to manage visibility of the profile box
    let isProfileOpen = false;
  
    // Functions to add new skills
    let newSkillHave = "";
    let newSkillLearn = "";
    let skillInputHave;
    let skillInputLearn;
    
    function toggleProfile() {
      isProfileOpen = !isProfileOpen;
    }
  
    function addSkillHave() {
      if (newSkillHave.trim()) {
        skillsHave = [...skillsHave, newSkillHave.trim()];
        newSkillHave = "";
        skillInputHave.focus(); // Refocus the input
      }
    }
  
    function addSkillLearn() {
      if (newSkillLearn.trim()) {
        skillsLearn = [...skillsLearn, newSkillLearn.trim()];
        newSkillLearn = "";
        skillInputLearn.focus(); // Refocus the input
      }
    }
  
    // Functions to remove skills
    function removeSkillHave(index) {
      skillsHave = skillsHave.filter((_, i) => i !== index);
    }
  
    function removeSkillLearn(index) {
      skillsLearn = skillsLearn.filter((_, i) => i !== index);
    }
  </script>
  
  <div class="profile-toggle">
    <img
      src={pfpUrl}
      alt="Profile Picture"
      class="profile-pfp"
      on:click={toggleProfile}
      title="Click to toggle profile"
    />
  
    {#if isProfileOpen}
      <div class="profile-box visible">
        <img src={name} alt={name} />
        <p><strong>Username:</strong> {username}</p> <!-- Displaying the username -->
  
        <div class="skills-section">
          <div class="skills-list">
            <h3>Skills I Have:</h3>
            <ul>
              {#each skillsHave as skill, index}
                <li>
                  {skill} <button on:click={() => removeSkillHave(index)} title="Remove skill">✖</button>
                </li>
              {/each}
            </ul>
            <input
              type="text"
              placeholder="Add a skill"
              bind:value={newSkillHave}
              bind:this={skillInputHave}
              on:keydown={(e) => e.key === "Enter" && addSkillHave()}
            />
            <button on:click={addSkillHave} disabled={!newSkillHave.trim()}>Add</button>
          </div>
  
          <div class="skills-list">
            <h3>Skills to Learn:</h3>
            <ul>
              {#each skillsLearn as skill, index}
                <li>
                  {skill} <button on:click={() => removeSkillLearn(index)} title="Remove skill">✖</button>
                </li>
              {/each}
            </ul>
            <input
              type="text"
              placeholder="Add a skill"
              bind:value={newSkillLearn}
              bind:this={skillInputLearn}
              on:keydown={(e) => e.key === "Enter" && addSkillLearn()}
            />
            <button on:click={addSkillLearn} disabled={!newSkillLearn.trim()}>Add</button>
          </div>
        </div>
      </div>
    {/if}
  </div>
  
  <style>
    .profile-toggle {
      position: fixed;
      top: 0px;
      right: 0px;
      padding: 20px;
    }
  
    .profile-pfp {
      width: 60px;
      height: 60px;
      border-radius: 50%;
      object-fit: cover;
      border: 2px solid #5271ff;
      cursor: pointer;
    }
  
    .profile-box {
      position: absolute;
      top: 100px;
      right: 20px;
      width: 300px;
      border: 1px solid #ddd;
      border-radius: 8px;
      background-color: #fff;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      padding: 16px;
      opacity: 0;
      transform: translateX(10px);
      transition: opacity 0.3s ease, transform 0.3s ease;
    }

    .profile-box img {
      width: 260px; /* Adjust the size as needed */
      object-fit: cover; /* Ensures the image fits nicely within the bounds */
      margin-top: 16px; /* Add some spacing below the image */
    }
  
    .profile-box.visible {
      opacity: 1;
      transform: translateX(0);
    }
  
    .skills-section {
      margin-top: 16px;
    }
  
    .skills-list {
      margin-bottom: 16px;
    }
  
    h3 {
      margin-bottom: 8px;
    }
  
    ul {
      list-style: none;
      padding: 0;
      margin-bottom: 8px;
    }
  
    li {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 4px;
    }
  
    button {
      background-color: #ffbd59;
      color: white;
      border: none;
      border-radius: 4px;
      padding: 4px 8px;
      cursor: pointer;
      font-size: 0.8rem;
    }
  
    button:hover {
      background-color: #d32f2f;
    }
  
    input {
      width: calc(100% - 80px);
      padding: 4px;
      font-size: 1rem;
      border: 1px solid #ccc;
      border-radius: 4px;
      margin-right: 8px;
    }
  
    input:focus {
      outline: none;
      border-color: #0077cc;
      box-shadow: 0 0 5px rgba(0, 119, 204, 0.5);
    }
  
    @media (max-width: 600px) {
      .profile-box {
        right: 10px;
        top: 80px;
        width: 90%;
      }
    }
  </style>
  