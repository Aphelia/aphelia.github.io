---

layout: default
title: "Issue Postmortem: August 18th"
description: "A detailed explanation on the connection issues on August 18th."
permalink: /2020-8-18-issue-postmortem/

---

Yesterday, on August 17th, I updated Aphelia Beta on our GCP aphelia-00 node. When doing this, I transferred over the files that contained guild specific data 
and configuration files to beta. However, it looks like moved the files instead of copying them. This meant that a lot of data was no longer accessible for 
Aphelia stable users. However, this didn't affect users until today, as we cache all data in memory, but the cache isn't persistent throughout restarts. 
Additionally, when a user modifies data of a module with cached data, it writes the cache to disk. This is why it didn't affect all users. However, when we ran 
a global restart, some guilds didn't have the data written to disk, thus causing some guilds to lose data. I'm very sorry for this issue, and will make sure 
it doesn't happen again.

An unrelated issue also happened on beta. I forgot to allow all users to use it. That was unrelated and was due to a misconfigured firewall.
