# zenon-network/twitter

Welcome to the Zenon Network's Twitter GitHub repository. This project allows you to create and manage tweets directly from this repository. Follow the instructions below to get started:

## The `tweets/` Folder

To create a new tweet, create a new `*.tweet` file in the `tweets/` folder.

### Example

Create a new file `tweets/dd-mm-yy-hello-world.tweet` with the content:

```
Hello, world!
```

### File Naming Convention
File names must follow the dd-mm-yy-tweet-name.tweet nomenclature. This format helps maintain a clear and organized structure, ensuring each tweet is easily identifiable by the date of creation and a descriptive name.

### File Naming Convention

File names must follow the `dd-mm-yy-tweet-name.tweet` nomenclature. For example, `12-06-24-hello-world.tweet`.


## Notes

- Only newly created files are handled; deletions, updates, or renames are ignored.
- `*.tweet` files will not be created for tweets you send out directly from twitter.com.
- If you need to rename an existing tweet file, please do so locally using [`git mv old_filename new_filename`](https://help.github.com/en/articles/renaming-a-file-using-the-command-line), otherwise it may be seen as deleted and added, which would trigger a new tweet.
- Your message must fit into a single tweet.



## Advanced Tweeting

Beyond tweeting out plain-text tweets, the twitter-together github action also supports creating polls, threading a chain of tweets, and adding images to tweets.

### Polls

Polls can be included directly in the body of tweet like so:

```
What is your favorite color?

( ) Red
( ) Blue
( ) Green
```

A poll can also be defined in frontmatter, rather than in the tweet body, like so:

```
---
poll:
  - Red
  - Blue
  - Green
---

What is your favorite color?
```

### Include Media

To include media items with your tweet, include the `media` frontmatter item as an array with each item having a `file` property and an optional `alt` property. The `file` property should be the name of a file within the `media` directory of your repository (same level as the `tweets` directory).

(Note: Although alt text can be set in frontmatter, it is not yet actually passed to Twitter due to library limitations).

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

### Thread a Chain of Tweets

To thread a chain of tweets, use `---` to delimit each tweet in the file. You can optionally set `threadDelimiter` in the frontmatter to change the delimiter for the next tweet in the thread. Each tweet in a thread supports its own frontmatter.

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

## Questions?

If you have any further questions or suggestions, please join the conversation on our [Discord](https://discord.gg/zenonnetwork).
