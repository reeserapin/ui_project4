<script>
  import SkillBox from './SkillBox.svelte';

  let users = [
    {
      name: "Alice Johnson",
      skillsHave: ["JavaScript", "Svelte", "CSS", "Web Development"],
      skillsLearn: ["Video Editing", "Digital Art", "Photography"],
      imageUrl: '/headshot1.jpg'
    },
    {
      name: "David Jackson",
      skillsHave: ["Automotive Repair", "Marketing"],
      skillsLearn: ["Personal Fitness Training", "Cooking/Baking", "Legal Document Preparation"],
      imageUrl: '/headshot2.jpg'
    },
    {
      name: "Deepshikha Jaya",
      skillsHave: ["Plumbing", "Basic Home Repairs", "Carpentry"],
      skillsLearn: ["Electrical Work", "Bookkeeping", "Copywriting"],
      imageUrl: '/headshot3.jpg'
    },
    {
      name: "Ho Yin",
      skillsHave: ["Welding", "Wood Carving", "Juggling"],
      skillsLearn: ["Career Coaching", "Event Planning", "Grant Writing"],
      imageUrl: '/headshot4.png'
    },
    {
      name: "Mike Naber",
      skillsHave: ["Personal Fitness Training", "Gardening"],
      skillsLearn: ["Childcare/Babysitting", "Meal Prep", "Sewing"],
      imageUrl: '/headshot5.jpg'
    },
    {
      name: "Rehema Nia",
      skillsHave: ["Pet Care and Training", "Hairdressing/Grooming"],
      skillsLearn: ["Voice Acting/Narration", "Survival Skills"],
      imageUrl: '/headshot6.jpg'
    },
    {
      name: "Jensine Isaksen",
      skillsHave: ["Bartering/Negotiation", "Musical Instrument Harp"],
      skillsLearn: ["Drone Operation", "Ethical Hacking"],
      imageUrl: '/headshot7.jpg'
    },
    {
      name: "Monique Carothers",
      skillsHave: ["Underwater Basket Weaving", "Ball Clay Pottery", "French"],
      skillsLearn: ["Oil Painting", "Sculpting"],
      imageUrl: '/headshot8.png'
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