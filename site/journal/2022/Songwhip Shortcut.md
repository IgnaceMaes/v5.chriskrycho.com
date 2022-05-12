---
title: A Songwhip Shortcut
subtitle: A tiny bit of automation because I really enjoy sharing music with friends.
tags:
    - music
    - automation
summary: >
    I built a Shortcut (that works on macOS, iOS, or iPadOS) to generate Songwhip links from the currently-playing music track.
qualifiers:
    audience: >
        People who like making computers do cool things for them; also people who like sharing music with friends.

---

For a few years now, I have been a fan of the free online service [Songwhip](https://songwhip.com). You paste in a link to a given song or album on any major music service (Spotify, Apple Music, etc.), and it generates a page which links to *all* the music services. I used this for [my own fanfare](https://songwhip.com/chriskrycho/fanfare-for-a-new-era-of-american-spaceflight), but even more than that I really like using this as a way to share music with friends. When I hear something I really like, I can just make a Songwhip link to hand them, and whatever music service *they* use, they can get to it directly from that link!

A little while back, I thought it would be nice to automate that. Instead of needing to copy the <abbr title="universal resource link">URL</abbr> from the music player (in my case Apple Music, which makes that an annoyingly fiddly operation), then open the Songwhip site and paste in the <abbr>URL</abbr>, then copy the *resulting* <abbr>URL</abbr> and share that with a friend. I mean: it’s *fine*, but… computers are really good at this kind of thing, and Apple’s introduction of [Shortcuts](https://support.apple.com/guide/shortcuts-mac/intro-to-shortcuts-apdf22b0444c/mac) to macOS in the current release had me thinking… could I make this basically *trivial*?

The answer is *yes*, and it took me less than five minutes:

1. Apple supplies a **Copy Apple Music Link** example shortcut in their gallery. This gave me
2. Songwhip has [a simple <abbr title="JavaScript Object Notation">JSON</abbr> <abbr title="application programming interface">API</abbr>](https://songwhip.com/faq#does-songwhip-have-an-api) which just responds to <abbr title="Hypertext Transfer Protocol Secure">HTTPS</abbr> requests with a handy blob you can use.

Given (1), all I needed to do was add a few more steps to the workflow:

- Add a new **Get contents of <abbr>URL</abbr>** block:
    - set the <abbr>URL</abbr> to `https://songwhip.com`
    - set the type of the request to `POST`
    - add a "request body" of type <abbr>JSON</abbr> with a single key of `url` and a corresponding value of the <abbr>URL</abbr> created by the original **Copy Apple Music Link** shortcut

- Add a **Get dictionary from...** block which takes the result of the previous step and turns it into a local "dictionary" object. This takes that <abbr>JSON</abbr> response from Songwhip and formats it into data I can work with directly.

- Add a block to **Get *Value* for *`url`* in *Dictionary*** to pull the *Songwhip* `url` out of the response data.

- Add a block to **Copy *Dictionary Value* to clipboard**. This does exactly what you would expect: puts the generated <abbr>URL</abbr> on the clipboard so I can share it with friends!

Net, [here is the shortcut](https://cdn.chriskrycho.com/file/chriskrycho-com/workflows/Apple%20Music%20%E2%86%92%20Songwhip.shortcut), which you can import and use (and customize, if you like) yourself! One big caveat, though: *it only works with songs that are in your library.* If you are listening to something via the “Apple Music” section of the app *or* something you *haven’t* added to your library, it will just… silently not work. 🧐 You must be listening to it via the “Library” section of the app.

As a bonus: [Raycast](https://www.raycast.com) has built-in support for running Shortcuts, so all I have to do is launch it with <kbd>⌘</kbd><kbd>␣</kbd> and type "Songwhip" and then hit <kbd>↩</kbd>, and it runs it on whatever song is currently playing.