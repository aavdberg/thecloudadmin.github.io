---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Running Your Hugo Blog on Azure WebApp With Mime-types Json and Manifest"
titlelink: ""
subtitle: ""
summary: "When you run your Hugo blog with Azure Webapp on Windows, the mime-type .json and .webmanifest are not configured by default. So will explain in this blog how you can add them to your Azure Webapp running on Windows"
authors: []
tags: [Azure WebApp, Hugo, Mime-type, json, manifest]
categories: [Azure]
date: 2020-05-12T17:38:19+02:00
lastmod: 2020-05-12T17:38:19+02:00
featured: false
draft: false
profile: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []

# Example of posting a picture with shortcode
#
# {{< figure src="images/BackgroundEffectTeams-007.png" title="" lightbox="true" >}}
#
---

## Intro

I switched some weeks ago over to another Hugo theme from Academic, and then someone attended me on the fact that my search on the site was not working. So I asked a question on the support forum of the Academic theme and got the direction to solved the problem.

By default when you run your Azure Web App on Windows the mime-types .json and .webmanifest are not configured so this means that they are not available on your website to the public.

## Step-By-Step explained to fix it

You have to put the following in you web.config that is sitting in the wwwroot folder of your Azure Web App.

```xml
        <staticContent>
            <mimeMap fileExtension=".json" mimeType="application/json"/>
            <mimeMap fileExtension=".webmanifest" mimeType"application/manifest+json"/>
        </staticContent>
```

Because I deploy my blog generated with Hugo and use Azure DevOps with build and release pipelines to deploy it on Azure Web App running on Windows I put the web.config file in the ./static folder and the Hugo generator will put it in the wwwroot folder on the Azure Web App.

## Conclusion

after adding the correct mime-types to the web.config file and deploy it with Azure DevOps to my Azure Web App by doing a Git commit and Push that triggered the CD/CI in Azure DevOps the search engine started to work again on my Blog.

See the following search for this blog item on the keyword mime-type

{{< figure src="images/mime-type-001.png" title="" lightbox="true" >}}