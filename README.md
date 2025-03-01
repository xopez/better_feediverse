This repo is a copy and updated version of [edsu/feediverse](https://github.com/edsu/feediverse)

You can always view changes here: https://github.com/edsu/feediverse/compare/master...xopez:better_feediverse:master

## Description

*better_feediverse* will read RSS/Atom feeds and send the messages as Mastodon posts.
It's meant to add a little bit of spice to your timeline from other places.
Please use it responsibly.

## Install

    pip install better_feediverse

## Run

The first time you run *better_feediverse* you'll need to tell it your Mastodon
instance and get an access token which it will save in a configuration file. If
you don't specify a config file it will use `~/.better_feediverse`:

    better_feediverse

Once *better_feediverse* is configured you can add it to your crontab:

    */15 * * * * /usr/local/bin/better_feediverse    

Run `better_feediverse --help` to show the command line options.

## Post Format

You can customize the post format by opening the configuration file (default is
~/.better_feediverse) and updating the *template* property of your feed. The default
format is:

    {title} {url}

If you want you can use `{summary}` in your template, and add boilerplate text
like so:

    Bookmark: {title} {url} {summary}

`{hashtags}` will look for tags in the feed entry and turn them into a space
separated list of hashtags. For some feeds (e.g. youtube-rss) you should use `{link}` instead of `{url}`.

`{content}` is the whole content of the feed entry (with html-tags
stripped). Please be aware that this might easily exceed Mastodon's
default limit of 500 characters.