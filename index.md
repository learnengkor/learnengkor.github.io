---
layout: default
---
# Welcome to Learn Engkor!

Hi! This site is about learning Korean and English.

If you have anything to discuss, you can add your comments below:

<!-- Search Form -->
<form id="search-form">
    <input type="text" id="search-input" placeholder="Search posts...">
    <button type="submit">Search</button>
</form>

<!-- Search Results Container -->
<div id="search-results">
    <!-- Results will be dynamically added here -->
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const posts = [
        { title: "Post 1", content: "Content of Post 1..." },
        { title: "Post 2", content: "Content of Post 2..." },
        // Add more posts as needed
    ];

    const form = document.getElementById('search-form');
    const input = document.getElementById('search-input');
    const resultsContainer = document.getElementById('search-results');

    form.addEventListener('submit', function(event) {
        event.preventDefault();
        const searchTerm = input.value.toLowerCase();
        const filteredPosts = posts.filter(post => {
            return post.title.toLowerCase().includes(searchTerm) || 
                   post.content.toLowerCase().includes(searchTerm);
        });
        displaySearchResults(filteredPosts);
    });

    function displaySearchResults(results) {
        let html = '';
        if (results.length > 0) {
            results.forEach(post => {
                html += `<div class="search-result">
                            <h3>${post.title}</h3>
                            <p>${post.content}</p>
                        </div>`;
            });
        } else {
            html = `<p>No results found.</p>`;
        }
        resultsContainer.innerHTML = html;
    }
});
</script>
