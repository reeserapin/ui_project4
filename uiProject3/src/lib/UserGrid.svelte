<script>
  import SkillBox from './SkillBox.svelte';

  let users = [
    {
      name: "Alice Johnson",
      skillsHave: ["JavaScript", "Svelte", "CSS"],
      skillsLearn: ["Python", "Machine Learning"],
      imageUrl: '/headshot1.jpg'
    },
    {
      name: "Dave Jackson",
      skillsHave: ["Python", "Data Analysis"],
      skillsLearn: ["React", "Web Design"],
      imageUrl: '/headshot2.jpg'
    },
    {
      name: "Deepika Patel",
      skillsHave: ["Graphic Design", "Illustration"],
      skillsLearn: ["UI/UX Design", "3D Modeling"],
      imageUrl: '/headshot3.jpg'
    }
  ];
  let searchTerm = ''; // For capturing the search input

// Filter users based on the search term
$: filteredUsers = users.filter(user => 
  user.name.toLowerCase().includes(searchTerm.toLowerCase()) ||
  user.skillsHave.some(skill => skill.toLowerCase().includes(searchTerm.toLowerCase())) ||
  user.skillsLearn.some(skill => skill.toLowerCase().includes(searchTerm.toLowerCase()))
);
</script>

<div class="search-container">
<input 
  type="text" 
  placeholder="Search users by name or skill..." 
  bind:value={searchTerm} 
/>
</div>

<div class="user-grid">
{#each filteredUsers as user}
  <SkillBox 
    name={user.name} 
    skillsHave={user.skillsHave} 
    skillsLearn={user.skillsLearn} 
    imageUrl={user.imageUrl} 
  />
{/each}
</div>

<style>
.search-container {
  margin: 16px;
  text-align: center;
}

.search-container input {
  width: 80%;
  padding: 8px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.user-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 16px;
  padding: 16px;
}
</style>