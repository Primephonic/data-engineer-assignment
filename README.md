# Primephonic Data-Engineering coding challenge
Thanks for your interest in Primephonic and for taking the time to do our data-engineering coding challenge. We hope you enjoy developing it as much as we did :)

## Background
A major part of our business hovers around data management. From periodically ingesting and processing new content provided by music labels, to gathering real-time analytics events, to generating usage and financial reports, to feeding machine learning algorithms, to everything in between.

The role of a data engineer at Primephonic is to build the backbone of our data infrastructure, ensure that all data flows in and out efficiently, and is made available to the rest of the company, especially the data scientists to consume.

This assignment is meant to evaluate how you approach a concrete data engineering problem you might encounter as part of your daily routine at Primephonic.

## Task
We've recently rolled out fully personalized playlists for some users. These playlists are generated by our machine learning algorithms, and created based exclusively on each user's personal listening behaviour. These personalized playlists make up one of multiple ways a user can consume music within the Primephonic app - other options are for example: manually curated playlists, playlists created by the users themselves, albums, recordings, etc.

We would like to understand how popular this feature is. Lucky us, we already have an existing analytics backend which tracks every single stream.

Your job is to build a data pipeline which will allow our business users to measure how this feature is being used. For this, we expect you to build at least the following:

### 1. Data consolidation
You've been given access to a randomized and anonymized subset of some of our data. They are in 2 files:

| Filename | Format | Explanation |
| --- | --- | --- |
| `playlists.ndjon` | `NDJSON` | A subset of the output generated by our personalized recommendations engine. Each line represents a single user, and 3 generated playlists for them.|
| `events.csv` | `CSV` | A subset of the streams generated by our users. Things like seconds streamed, the id of the track (song), etc. |

You might have noticed that each user in `playlists.ndjon`, is assigned 3 playlists which are unique to them (meaning: `playlist_01` of user X is not the same as `playlist_01` of user Y - same name, but different content).

You might have also noticed that `events.csv` contains every single streamed event possible (from playlists, but also albums, etc). At this time, however, our data analysts are only interested in analysing the effects of the personalized playlists, which are expressed as having a `listeningContext` of `playlist_XX` (where `XX` is a decimal).

Your task is to merge these 2 data sources into a single suitable data source, which exposes *only* data regarding the personalized playlists (everything else should be excluded). The data should be modeled in such a way that it can be queried by a business user without too much technical knowledge. They should be able to answer the question "Which works were recommended to user X" by running a simple query, without having to join datasets, or interpret meaning of ids, etc.

### 2. Report creation
With the newly created data source, your task is to now create a report/dashboard (in any technology/tool of your choice - can also be text-based), which displays a summary of the total number of seconds consumed by each of the personalized playlists.

## Requirements
You may use any programming language, library, database, etc. of your choice, as long as there is a:
1. Clear explanation of why you chose it
2. We can run the assignment ourselves, so please make sure that all aspects of this assignment are easily reproduceable.
