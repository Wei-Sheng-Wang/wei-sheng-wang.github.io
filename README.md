# My Research Blog

This is my personal blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, deployed automatically to GitHub Pages.

## Local Development

1. Install Hugo:
   ```bash
   brew install hugo  # macOS
   ```

2. Clone this repository:
   ```bash
   git clone --recursive YOUR_REPOSITORY_URL
   ```

3. Start the local development server:
   ```bash
   hugo server -D
   ```

4. View your site at http://localhost:1313/

## Creating New Posts

To create a new blog post:

```bash
hugo new content posts/my-new-post.md
```

## Deployment

The blog is automatically deployed to GitHub Pages when changes are pushed to the main branch.

## Customization

To customize the site:

1. Edit `hugo.toml` for site configuration
2. Modify theme settings in `hugo.toml`
3. Add content in the `content/posts` directory

## Theme Documentation

For more information about the PaperMod theme, visit:
https://github.com/adityatelange/hugo-PaperMod/wiki 