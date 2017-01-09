---
layout: post
title: 📝 Teamline - Setup
excerpt: Building an open source tool for teams using technologies like Swift on the server side, and ReactJS for the frontend.
tags: [teamline, setup, vapor, swift]
comments: true
image:
  feature: headers/teamline.jpg
  credit: Photo by Samuel Scrimshaw
sitemap   :
  priority : 0.9
  isfeatured : 1
---

2017 is here. One of my purposes for this year was to learn some frontend development and a technology that I wasn't familiar with. I was very excited about React and building web interfaces using components, and using Swift on the server side. **What if I could combine both of them in a single project?** Then I had an idea that I'd been thinking about for a long time came to my mind, **Teamline**. I'd read from different startups that even using products like Slack, Hipchat, or any other communication tool, they missed a tool that allowed them stay in sync with the other teams and projects. A tool that kept people informed about the things that were going on at the company.

> Imagine the Facebook timeline format but for projects, where you can see all your projects, and posts from your colleagues, comment on them, like them... And at the end of the day, only if you are interested, you'd get a report about the day.

Real-time communication and email can be exhausting. It happened to me before that I tried to keep up with everything and I ended up giving up and focusing on my day-to-day work. However, in doing that, I felt disconnected from everything around me. What if I could have a place where I could check that information? [GitHub](https://github.com) uses its own solution that they developed because they had a similar problem. Other companies like [Zappier](https://zappier.com) use a Wordpress template, [P2](https://p2theme.com/) that was developed for the same reason. 

My goal with this project was to learn and share my learnings that I hope can be useful for any other developer trying something similar. The project will be in open on [GitLab](https://gitlab.com) so you'll be able to check the source code, create pull-requests, open issues... I'll write a series of posts explaining all the steps that I'm taking to develop different components: decissions, implementation details, patterns...

I'll evolve the project with your feedback so I'm happy to share your thoughts and ideas to apply them to the project.

### Technologies

- **Backend:**
  - **[Swift (Vapor)](https://vapor.codes/)**: I'll use Swift and Vapor because I'm familiar with the language and I've heard so many things about Swift on the server side that I wanted to give it a try. I'd used Rails before for other backends and I didn't like it wasn't type safe and I was slower coding since I wasn't familiar with the Ruby APIs.
  - [**PostgreSQL**](https://www.postgresql.org/): I personally prefer to have a schema define and know the structure of the data that I'm currently saving in the database. That's why I preferred PostgreSQL instead of other solutions like MongoDB. A good point in favor of Vapor as a framework is that it provides drivers to interact with the most popular database technologies, like MySQL, MongoDB, PostgreSQL...
- **Frontend:**
  - I'll use [ReactJS](https://facebook.github.io/react/) from Facebook, [ES6](http://es6-features.org/), [Bootstrap 4](https://v4-alpha.getbootstrap.com/), [Redux](https://github.com/reactjs/redux), [Webpack](https://webpack.github.io/) for bundling all web resources and the frontend will be deployed to a [DigitalOcean](https://www.digitalocean.com/) instance that will be running an [Nginx](https://www.nginx.com/resources/wiki/) instance serving all the resources. Thanks [@jan](https://twitter.com/thedeftone) for all the tips and help.
- **iOS:**
  - In this case I'll go with the native approach and I'll code it in Swift. I'm familiar with the platform and the language so coding will be relatively straightforward to me.
- **Android:**
  - I'll use Java in this case. I coded for the platform a long time ago and I still remember a few things. I'll have to refresh what I knew.

> Domains `.com` are of cool and demanded but since Teamline will born in Spain, the domain `teamline.es` is the perfect fit for the project.

### Backend setup

In this first post I'll explain how I setup and deploy the backend to start working on it.

#### Installing Vapor Toolbox

Vapor comes with a command line tool that automate some common tasks. I installed it using brew:

{% highlight bash %}
brew install vapor/tap/toolbox
{% endhighlight %}

Once installed, `vapor` prints out all the available options.

#### Creating the project

Creating the project with Vapor Toolbox is very simple:

{% highlight bash %}
vapor new teamline
{% endhighlight %}

The tool will create the project under `./teamline`. Since I'll push the project to [GitLab](https://gitlab.com) we can use its continuous integration component. It needs the project to define the build steps in a `.gitlab-ci.yml` file. I created the file in the project with the following content:

{% highlight yaml %}
image: swiftdocker/swift 
stages:   
  - build 
build:   
  stage: 
    build   
  script:   
  - swift build
{% endhighlight %}

It specifies the stages that have to be run and the Docker container where all these steps will be executed. `swiftdocker/swift` is an Ubuntu image that contains Swift already installed.

I made sure the project compiled with:

{% highlight bash %}
swift build
{% endhighlight %}

#### Deploy

I'll deploy teamline to [Heroku](https://heroku.com) that integrates easily with other services. I installed [Heroku CLI]() and then use Vapor to setup Heroku for the project:

{% highlight bash %}
vapor heroku init
{% endhighlight %}

I specified `teamline` as a name and told the command to deploy it to Heroku. After a while I got the backend deploy and I can access it from the web browser, [http://teamline.herokuapp.com/](http://teamline.herokuapp.com/)

### What's next

Once we have the backend ready and deployable in the next article I'll go through the steps to setup a PostgreSQL database, define the models that I'll need for Teamline, and implement the controllers that will define the API of our backend.

Happy coding! :tada:


#### You can check out the project on GitLab: [caramba/teamline-backend](https://gitlab.com/caramba/teamline-backend)

