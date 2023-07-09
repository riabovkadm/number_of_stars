// Import the 'axios' library for making HTTP requests
const axios = require('axios');

// Function to retrieve repository information for a GitHub user
async function getRepositories(username) {
  try {
    // Make a GET request to the GitHub API to fetch user repositories
    const response = await axios.get(`https://api.github.com/users/${username}/repos`);

    // Extract the repository data from the response
    const repositories = response.data;

    // Output repository information
    repositories.forEach((repo) => {
      console.log(`Repository Name: ${repo.name}`);
      console.log(`Description: ${repo.description}`);
      console.log(`Language: ${repo.language}`);
      console.log(`URL: ${repo.html_url}`);
      console.log('---------------------------');
    });
  } catch (error) {
    console.error(`Error retrieving repositories for ${username}: ${error.message}`);
  }
}

// Call the function with a GitHub username
getRepositories('your-github-username');
