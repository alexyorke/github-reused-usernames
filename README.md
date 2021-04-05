# github-reused-usernames
Detect if a GitHub username was deleted and then re-registered. There is a high chance of false negatives but extremely low or no chance of false positives.

## Where does the data come from?

The data comes from gharchive.org. I went through all 1.1TB or so from 2011 to the end of 2020, collected all usernames and user ids, and then found all usernames that were associated to more than one user id, case-insensitively. To help with privacy, each username is SHA256 hashed, lowercased, then truncated to 80 bits. The hash is truncated to reduce the download size.

## Caveats
Some of the files on gharchive.org are not valid JSON files. I'm currently investigating those, and so the usernames in those files are not accounted for.

Also, if a user didn't do _anything_ on GitHub, then they won't be included in this list. There's no events for them on gharchive.org and so I don't have any data for them.

## Why would I want to use this?

If a username has been re-registered on GitHub, then the new user (under the old username) could create a new repository with the same name as one of the previous owners repos. This would normally be confusing, as the new user may have a different repo than the older user.
