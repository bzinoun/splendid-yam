---
title: ' Move from an IBM Cloud account to another '
date: '2019-12-16T09:43:41.286Z'
excerpt: ''
thumb_img_path: >-
  https://res.cloudinary.com/practicaldev/image/fetch/s--zMROcrsX--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://res.cloudinary.com/practicaldev/image/fetch/s--AGcz5IuM--/c_imagga_scale%2Cf_auto%2Cfl_progressive%2Ch_420%2Cq_auto%2Cw_1000/https://thepracticaldev.s3.amazonaws.com/i/1xeoxs9yj5z6d16aw8fx.png
comments_count: 0
positive_reactions_count: 7
tags:
  - cloud
  - migration
  - devops
  - ibmcloud
canonical_url: 'https://dev.to/bzinoun/move-from-an-ibm-cloud-account-to-another-4kj0'
template: post
---
A few weeks ago, we had to move from an IBMCloud account to another , the cause was some enterprise constraints , you know the movie 🤷‍♂‍ .

As IBMCloud doesn’t provide tools out of the box for it, our migration was based on our daily CI/CD pipeline! Wow 🤦‍♂‍

Now, let's see what we need to move to the new Cloud:

➡️ 30 CloudFoundry
➡️ 10 PostgreSql
➡️ 2 MongoDB
➡️ 3 AppID (OPIDC)
➡️ 4 domain names

Okey 49 assets to move, seems good.

Now we have seen the most asset we have, the idea is to use CI/CD pipelines for *most* of our deployments.
 
So, what's about our application’s pipeline:

- ✅ Some applications are deployed with GitlabCI pipeline => should be OK
- ❌ Some applications are deployed with IBMCloud Devops pipeline => which is not cloud agnostic 
- ❌ No Infrastructure as code for BDD, AppId ...etc. => Hmm manually provisioning ?  
- ✅ Data migration? all our assets have an API for import/export => it's should be OK. 

We have some bad and good thinks, moving all that stuff with a minimal down want be the best way , so without too much thinking 

💡 Blue Green deployment is the best way 
*More about blue green deployment from Martin Fowler  [here](https://martinfowler.com/bliki/BlueGreenDeployment.html)* 

![Dak'aa](https://media.giphy.com/media/d3mlE7uhX8KFgEmY/giphy.gif)

The Gif below describe in visual way how we proceed: 

![migrationgif](https://thepracticaldev.s3.amazonaws.com/i/bwr1poqwae3xayog2xbn.gif)

The process can be splitted to 6 steps describes as below: 

**Step 1** - unifying our deployment Pipeline by moving all our CI/CD pipeline to GitlabCI. 

**Step 2** - Move all non-production assets . As we are working in an agile mode we move the dev environment first then, when needed, staging , sandbox

**Step 3** - Move the production assets, then data migration, then push the provisional production URL to the Business analyst / Product Owner for a Go/No GO 

**Step 4** - Once we have the GO -> Migrate the domain name from the legacy cloud to the New IBMCloud 

**Step 5** - Remove the death pipeline code , and remove the old assets from legacy Cloud 

**Step 6** Celebrate with the Team. 🎊 🎉🎊 🎉

So, without going too deep into details of every step , this how we do the work . 

---
In the end, it's been not easy, and having a devops culture helps a lot and i can resume what we have learn : 

1- **we have to be cloud agnostic:** 
 A toolchain must be a cloud agnostic. If we want a change our 
  deployment strategy, it must me smooth.

2 - **Devops culture is a must**
The pipeline source must be versioned, involved with the code source. **The dev Team is the owner of the pipeline**

3 - **Start Easy** 
  Dev environment first, as we work on agile , the other environments will be **deployed in an iterative and incremental way**

4 - **If it’s hard manually, then script it .**
  Special attention to the Data migration for every type of asset. ( AppId , SQL , NoSql , Cloud object Storage …etc ) 

That's all folks, and how will you do in the same situation ?



*[This post is also available on DEV.](https://dev.to/bzinoun/move-from-an-ibm-cloud-account-to-another-4kj0)*


<script>
const parent = document.getElementsByTagName('head')[0];
const script = document.createElement('script');
script.type = 'text/javascript';
script.src = 'https://cdnjs.cloudflare.com/ajax/libs/iframe-resizer/4.1.1/iframeResizer.min.js';
script.charset = 'utf-8';
script.onload = function() {
    window.iFrameResize({}, '.liquidTag');
};
parent.appendChild(script);
</script>    
