# GitHub Profile Setup Instructions

This guide will help you deploy your professional GitHub profile README with automated blog post updates.

## Prerequisites

- GitHub account (awoods187)
- Git installed locally
- Command line access

## Step 1: Create the GitHub Repository

GitHub profiles use a special repository naming convention where the repository name matches your username.

1. Go to [GitHub](https://github.com/new)
2. Create a new repository named **`awoods187`** (must match your username exactly)
3. Set it to **Public** (required for profile READMEs)
4. **Do NOT** initialize with README, .gitignore, or license (we'll push our own)
5. Click "Create repository"

## Step 2: Initialize and Push Your Profile

Navigate to the profile directory and push to GitHub:

```bash
cd /Users/andrewwoods/claude-andyw/awoods187-profile

# Initialize git repository
git init

# Add all files
git add README.md .github/

# Create initial commit
git commit -m "Initial commit: Professional GitHub profile with automated blog updates"

# Add GitHub remote (replace with your actual repo URL)
git remote add origin https://github.com/awoods187/awoods187.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Step 3: Verify Profile Display

1. Go to your GitHub profile: https://github.com/awoods187
2. You should see your new README displayed prominently on your profile page
3. The blog posts section will initially show the placeholder comments

## Step 4: Test the GitHub Action

The workflow is configured to run daily, but you should test it manually first:

1. Go to your repository: https://github.com/awoods187/awoods187
2. Click on the **Actions** tab
3. Click on "Latest blog post workflow" in the left sidebar
4. Click the **Run workflow** button (on the right side)
5. Click the green **Run workflow** button in the dropdown
6. Wait 30-60 seconds and refresh the page
7. You should see a workflow run in progress or completed

## Step 5: Verify Blog Posts Appeared

After the workflow completes:

1. Go back to your repository's main page
2. Check the README.md file
3. The section between `<!-- BLOG-POST-LIST:START -->` and `<!-- BLOG-POST-LIST:END -->` should now contain your latest blog posts
4. Visit your profile (https://github.com/awoods187) to see the updated README

## Step 6: Customize the Content

You can edit the README.md directly on GitHub or locally:

### To update manually-managed sections:

```bash
# Edit the README
cd /Users/andrewwoods/claude-andyw/awoods187-profile
# Edit README.md with your preferred editor
# Update sections like "What I'm Building" or "Current Focus"

# Commit and push changes
git add README.md
git commit -m "Update current focus areas"
git push
```

### To update the workflow settings:

Edit `.github/workflows/blog-post-workflow.yml` to change:
- `max_post_count`: Number of blog posts to display (currently 5)
- `template`: How each blog post appears
- `date_format`: Date display format
- `cron`: Schedule (currently midnight UTC daily)

## Troubleshooting

### Workflow not running automatically?

- Check that the repository is public
- Verify the workflow file is in `.github/workflows/` directory
- Check the Actions tab for any error messages

### Blog posts not updating?

- Verify your RSS feed is accessible: https://andywoods.me/rss.xml
- Check the workflow run logs in the Actions tab
- Ensure the blog-post-workflow has write permissions (should be automatic for public repos)

### Want to change the update frequency?

Edit the `cron` line in `blog-post-workflow.yml`:
- `'0 0 * * *'` - Daily at midnight UTC
- `'0 */6 * * *'` - Every 6 hours
- `'0 0 * * 0'` - Weekly on Sunday
- `'0 0 1 * *'` - Monthly on the 1st

Use [crontab.guru](https://crontab.guru/) to help create cron schedules.

## Maintenance

### Weekly: Review "What I'm Building"
Update the current focus areas to reflect what you're actively working on.

### Quarterly: Update Impact Metrics
Refresh the numbers in the Impact section as your work progresses.

### As Needed: Adjust Technical Stack
Add or remove badges as your tech stack evolves.

## Advanced: Adding More Automation

If you want to add more automated sections (like GitHub stats, recent commits, etc.), consider these popular GitHub Actions:

- [github-readme-stats](https://github.com/anuraghazra/github-readme-stats) - Stats and language cards
- [github-readme-streak-stats](https://github.com/DenverCoder1/github-readme-streak-stats) - Contribution streaks
- [waka-readme](https://github.com/athul/waka-readme) - Coding time stats from WakaTime

## Questions or Issues?

- Check GitHub Actions documentation: https://docs.github.com/en/actions
- Review blog-post-workflow docs: https://github.com/gautamkrishnar/blog-post-workflow
- Verify your RSS feed structure at: https://validator.w3.org/feed/

---

**Note**: The automation is designed to be low-maintenance. Once set up, your blog posts will update automatically daily, and you only need to manually update the other sections when your focus or achievements change.
