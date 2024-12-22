# Linkedin-autoliker
This automatically likes all linkedin posts 

How to use
> Go to Linkedin feed
> 
>
> Navigate to your browser console
>
> Paste the below script

// Function to continuously like posts
function autoLikeFeedPosts() {
setTimeout(() => {
    // Select all posts on the current feed (you might need to adjust the selector if needed)
    const posts = document.querySelectorAll('.feed-shared-update-v2');
    
    if (posts.length === 0) {
      console.log("No posts found.");
      return;
    }

    posts.forEach((post, index) => {
      // Find the "Like" button inside the post
      const likeButton = post.querySelector('button[aria-label="React Like"]:not(.react-button--active)');
      
      // If the "Like" button is found and not already liked
      if (likeButton) {
        console.log(`Liking post #${index + 1}`);

        // Click the like button to like the post
        likeButton.click();
      } else {
        console.log(`Post #${index + 1} is already liked or no "Like" button found.`);
      }
    });

    // Scroll down to load more posts
    window.scrollBy(0, window.innerHeight);  // Scroll down by the height of the page

    // Retry after 5 seconds to interact with new posts
    setTimeout(autoLikeFeedPosts, 5000);  // Call the function again after 5 seconds
    
    }, 3000);  // Wait for posts to load before interacting
    }
    // Start the process
    autoLikeFeedPosts();
