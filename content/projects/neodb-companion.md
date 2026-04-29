+++
title = 'neodb-companion'
date = 2025-04-29T16:08:26+01:00
draft = false
tags = ['project', 'neodb', 'kotlin']
+++

A self-hosted companion server for [NeoDB](https://neodb.net/).

NeoDB Companion connects to any NeoDB account via OAuth and reads the user's movie and TV show wishlists. It then cross-references those items against user's countries' release dates to build a personalised iCal calendar (.ics) of upcoming releases, which it serves publicly over HTTP. Users can also opt-in to receive periodical email notifications when a wishlisted title is about to release.

A simple web UI lets each user configure their preferences (language, country, email notifications) and find their public calendar URL to subscribe to from any calendar app.

### Links

Find the source code on [Codeberg](https://codeberg.org/manglaneso/neodb-companion)