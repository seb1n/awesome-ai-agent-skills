---
name: social-media-posting
description: "Post content to social media platforms like Twitter, LinkedIn, and Facebook."
license: MIT
---

## Description

This skill allows the agent to post content to various social media platforms, enabling automated updates and engagement.

## Workflow

1.  **Authenticate:** The agent authenticates with the target social media platform using the appropriate credentials or API keys.
2.  **Compose:** The agent composes the content for the post, which can include text, images, and links.
3.  **Post:** The agent publishes the composed content to the specified social media channel.

## Usage

This skill is ideal for tasks that require automated social media management, such as:

-   Scheduling regular updates.
-   Sharing blog posts or articles.
-   Posting real-time notifications.

## Example

```
# Example: Post a tweet to Twitter

def post_tweet(api_key, api_secret, access_token, access_token_secret, message):
    # Authenticate with Twitter API
    auth = tweepy.OAuthHandler(api_key, api_secret)
    auth.set_access_token(access_token, access_token_secret)
    api = tweepy.API(auth)

    # Post the tweet
    api.update_status(message)
```
