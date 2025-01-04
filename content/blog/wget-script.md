---
title: "wget Script"
date: 2025-01-01T21:28:42-05:00
draft: true
featuredImage:
featuredImageAlt:

---
Here's a quick command line to check date modified of a website.

```
curl -s https://www.canada.ca/en/revenue-agency/services/forms-publications/forms/t2200.html | egrep dateModified
    <dd><time property="dateModified">2024-01-23</time></dd>
```

I need to check this website for the updated T2200 form so I have been manually checking it each day. Here's a commandline that should update once CRA updates the date within the dateModified attribute time tag.

This command line goes to the webstite ( the -s means silent without the transfer data) and I pipe it through egrep with DateModified to pull the time property="dateModified" tag.

The next task is to setup a cron job so I don't have to manually run this each day.
