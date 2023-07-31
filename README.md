# Connect your Hashnode blog's RSS to github portfolio
first of all watching [this video](https://youtu.be/BXC9_Nn34_s) or read [this post](https://imsadra.me/hashnode-blogs-on-github-profile)

then use this yaml code for github action:
```yaml
name: Hashnode Blog Posts
on:
  schedule:
    # Runs every 6 hours of the day
    - cron: '0 */6 * * *'
  workflow_dispatch:

jobs:
  update-readme-with-blog:
    name: Update this repo's README with the latest blog posts
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: gautamkrishnar/blog-post-workflow@master
        with:
          comment_tag_name: "BLOGPOSTS"
          feed_list: "<link-to-your-rss>"
          template: "$newline - $randomEmoji(💯,🔥,💫,🚀,🌮) [$title]($url)"
          commit_message: "recent posts section updated"
          gh_token: ${{ secrets.GITHUB_TOKEN }}
```
