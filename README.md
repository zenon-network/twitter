# Zenon Network Community Twitter Access

This repository allows you to request a tweet to be sent out via the @zenon_network Twitter account. To do so, simply create a `*.tweet` file in the `tweets/` directory of this repo. 

## Creating a New Tweet

1. Click this link: <kbd>[Create new tweet](../../../new/master/?filename=tweets/<your-path>.tweet)</kbd>
2. Replace `<your-path>` in the URL with the desired path of your file (e.g. `tweets/hello-world.tweet`).
3. Add your tweet content in the new file and commit it.

Example:

> Hello, world!

Subfolders are allowed as long as the file is in the `tweets/` directory and ends with the `.tweet` extension.

## Advanced Tweeting

In addition to plain text, you can also add polls, replies, retweets, quote-retweets, image attachments, and threaded tweets. Here's how to do it:

### Adding a Poll

Add your options at the end of the tweet in the following format:

> Here is some text
>
> ( ) option A  
> ( ) option B  
> ( ) option C  
> ( ) option D

Alternatively, use YAML frontmatter to define the poll:

```
---
poll:
  - Red
  - Blue
  - Green
---

What is your favorite color?
```

### Replying to a Tweet

Add the `reply` frontmatter item with the URL of the tweet you want to reply to:

```
---
reply: https://twitter.com/gr2m/status/1409601188362809349
---

@gr2m I love your work!
```

### Retweeting and Quote-Retweeting

Use the `retweet` frontmatter item with the URL of the tweet you wish to retweet. If you want to quote-retweet, simply add your comment after the frontmatter.

```
---
retweet: https://twitter.com/gr2m/status/1409601188362809349
---

twitter-together is awesome!
```

### Adding Media

To include media with your tweet, provide the `media` frontmatter item as an array where each item has a `file` property and an optional `alt` property. The file should be located in the `media` directory of your repo.

```
---
media:
  - file: cat.jpg
    alt: A cat
  - file: dog.jpg
    alt: A dog
---

Here are some cute animals!
```

### Creating a Thread

Use `---` to delimit each tweet in the file. Each tweet in a thread supports its own frontmatter.

```
---
media:
  - file: cat.jpg
    alt: A cat
  - file: dog.jpg
    alt: A dog
---

Here are some cute animals!

---
---
poll:
  - Cat
  - Dog
---

Which one is cuter?
```

## Notes

- The system only handles newly created files. Updates, deletions, or renames are ignored.
- If you need to rename an existing tweet file, use `git mv old_filename new_filename`.
- Your message must fit within Twitter's character limit.
- `*.tweet` files won't be created for tweets sent directly from Twitter.

## Need Help?

If you have any questions or suggestions, please [create a new issue](https://github.com/0x3639/action/issues/new).