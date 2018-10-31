# Blocky

A simple content blocker for macOS Safari.

![extension screenshot](/img/extension.png)
![app screenshot](/img/app.png)

## Install

Unzip Blocky.app into your `/Applications` folder.

To launch Blocky the first time, right-click it in Finder.app and open it manually.

When you launch Blocky.app, you'll need to activate its content blockers in
Safari's extensions panel.

![safari prefs](/img/safari-prefs.png)

## What & Why

Blocky uses WebKit's [Content Blocker API](https://webkit.org/blog/3476/content-blockers-first-look/) in an
effort to be a performant, minimal, yet competitive adblocker.

What's interesting about the Content Blocker system is that it compiles
allow/deny rules into lower level state machines which means that it can be
much more efficient than the ubiquitious JavaScript-based solutions.
The downside is that content blockers need to be recompiled on each change
(3-4 seconds on my Macbook Pro), like when adding/removing sites
from the whitelist.

This solution works across macOS (soon: and iOS) anywhere there's a web view.

Blocky.app is a bundle of:

-   Content blockers.
-   A macOS app for driving the blockers and the domain whitelist.
-   A Safari extension that offers quick whitelist toggling from Safari's menubar.

## Goals

Blocky's primary goal is to eliminate HTTP traffic, like requests to 3rd
party ad servers. This can mostly be done with a simple, global block list.

Blocky's secondary goal is to hide ad-related HTML elements on the most popular
websites. But the problem with HTML content blocking is that it tends to
lead to an append-only list of site-specific rules.

If you look at any of the big block lists online, you'll notice that
they are far, far more than just a list of domains to block. They are
complex DSLs that let people write site-specific rules, and a great
deal of their rules are per-site creature features.

In an effort to keep Blocky's rules simple, Blocky ships with generic
HTML-hiding rules.

## Features

-   **Per-domain whitelisting**:
    Sometimes content blocking interferes with
    the operation of a site like banking and airline websites. You can turn
    Blocky off on a domain (and its subdomains) by adding the domain to the
    whitelist.

TODO:

-   **Custom HTML hiding**:
    I'd like to eventually allow right-click -> "Block Element" customization per website.
-   **Custom content blocker rules**:
    Add raw content blocker rules to Blocky instead of relying solely on the rules that Blocky ships with.

## FAQ

-   **Why does it take so long to add/remove domains from my whitelist?**
    Blocky's whitelist is implemented as content blocker rules, so any
    changes to the whitelist will need to incur content blocker recompilation.

-   **Why does this repository only include binaries?**
    I'm planning on releasing the source code when I get Blocky on the App Store.
