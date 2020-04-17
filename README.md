[![Coverage Status](https://coveralls.io/repos/github/afinetooth/coveralls-demo-ruby/badge.svg?branch=travis)](https://coveralls.io/github/afinetooth/coveralls-demo-ruby?branch=travis)

# coveralls-ruby-demo for Travis CI

[Coveralls](https://coveralls.io/) demo project, using:

* [Ruby](https://www.ruby-lang.org/) — *Language*
* [Rspec](https://rspec.info/) — *Testing Library*
* [Simplecov](https://github.com/colszowka/simplecov) — *Code Coverage Library*

And:

* [GitHub](https://github.com/) — *SCM Service*
* [Travis CI](https://travis-ci.com/) — *CI Service*
* [Coveralls](https://coveralls.io/) — *Test Coverage Service*

# Welcome

You've gotten this far. Given that, we can assume:
   
<dl>
  <dt>1. You understand <a href="https://github.com/afinetooth/coveralls-demo-ruby#1-understand-test-coverage-in-this-project">how test coverage works in this project</a>.</dt>
  <dd>If not, start back at the <a href="https://github.com/afinetooth/coveralls-demo-ruby">master README</a>.</dd>

  <dt>2. You've chosen <a href="https://travis-ci.com/">Travis CI</a> as your CI Service.</dt>
  <dd>If not, head back to the <a href="https://github.com/afinetooth/coveralls-demo-ruby">master README</a> and <a href="https://github.com/afinetooth/coveralls-demo-ruby#which-ci-service-will-you-use">choose a different CI / branch</a>.</dd>
</dl>

# Travis CI & Coveralls

This project is configured to send test coverage results to [Coveralls](https://coveralls.io/) through [Travis CI](https://travis-ci.com/). 

Notice the Coveralls badge at the top of this page ([![Coverage Status](https://coveralls.io/repos/github/afinetooth/coveralls-demo-ruby/badge.svg?branch=travis)](https://coveralls.io/github/afinetooth/coveralls-demo-ruby?branch=travis)), which indicates we're successfully receiving coverage reports from Coveralls.

This doc will guide you through the configuration process.

## How to use this guide

Fork the [master branch](https://github.com/afinetooth/coveralls-demo-ruby/tree/master) of this project<sup>*</sup> and make your changes to it. Then use *[this branch](https://github.com/afinetooth/coveralls-demo-ruby/tree/travis)* to verify the changes you'll make. (Consider it your cheatsheet.)

<details>
   <summary><sup>*</sup> How to fork this repo</summary>
   
---

How-to (WIP).

---

</details>

### What we're doing

We're configuring the [base project](https://github.com/afinetooth/coveralls-demo-ruby/tree/master) to send test coverage results to [Coveralls](https://coveralls.io/) through [Travis CI](https://travis-ci.com/). Those changes are few and easy, and they're listed below. (And the final results are shown in the code above.)

So let's walk through each step:

## Config steps

1. Add repo to [Travis CI](https://travis-ci.com/)
2. Add `.travis.yml` to repo
3. Add repo to [Coveralls](https://coveralls.io/)
4. Add `.coveralls.yml` to repo

### 1. Add repo to Travis CI

<details>
   <summary>Do it. (WIP)</summary>
   
---
   
To add a public repo to Travis CI, you'll first need to sign up for the free version of the service, which you can do by going to [http://travis-ci.org/](http://travis-ci.org/) and singing up with your GitHub login:

![travis-ci-sign-up.png](../media/media/travis-ci-sign-up.png)

Alternately, if you're already a member, just sign in with your GitHub login:

![travis-ci-sign-in.png](../media/media/travis-ci-sign-in.png)

Once signed in, click on [Settings](https://travis-ci.org/account/repositories) or go to [https://travis-ci.org/account/repositories](https://travis-ci.org/account/repositories):

![travis-ci-settings-repos.png](../media/media/travis-ci-settings-repos.png)

If Travis doesn't already list all your public repos<sup>*</sup>, click the __Sync account__ button to refresh the list.

<details>
   <summary><sup>*</sup> What about private repos?</summary>

---

   [http://travis-ci.org/](http://travis-ci.org/) is the free version of the Travis CI service that's always free for public repos. To manage private repos, you'll want to join [http://travis-ci.com/](http://travis-ci.com/).
   
---

</details>

To add a repo to [Travis CI]((http://travis-ci.org/)), simply click the toggle control next to your repo:

![travis-ci-settings-repos-coveralls-demo-ruby.png](../media/media/travis-ci-settings-repos-coveralls-demo-ruby.png)

You can click on Settings next to your repo to see some basic configuration options for your repo, but for now let's leave everything there as-is:

![travis-ci-settings-repos-coveralls-demo-ruby-settings.png](../media/media/travis-ci-settings-repos-coveralls-demo-ruby-settings.png)

Now, the free version of Travis CI doesn't offer as much hand-holding as the paid version. Clicking on Documentation in the footer even takes you to docs for the paid version of the service, which aren't 100% applicable for the free version.

![travis-ci-docs.png](../media/media/travis-ci-docs.png)

Nevertheless, for us the [Getting started with GitHub](https://docs.travis-ci.com/user/tutorial/#to-get-started-with-travis-ci-using-github) instructions still apply (after the first three (3) steps aboout adding your repo to Travis CI):

![travis-ci-docs-getting-started-with-github.png](../media/media/travis-ci-docs-getting-started-with-github.png)

As described there, our next step is to add a `travis.yml` config file to our repo.

---

</details>

### 2. Add `.travis.yml` to repo

<details>
   <summary>Do it. (WIP)</summary>
   
---
   

According to the instructions, we need to:

> Add a `.travis.yml` file to your repository to tell Travis CI what to do. 

And luckily for us, the example is for Ruby and applies well to our project:

> The following example specifies a Ruby project that should be built with Ruby 2.2 and the latest versions of JRuby.

![travis-ci-docs-getting-started-with-github-sample-travis-yml.png](../media/media/travis-ci-docs-getting-started-with-github-sample-travis-yml.png)

With the exception that we're not using `jruby`. Instead, we're using "regular ruby", or the MRI (or "Matz") version of Ruby. So our `.travis.yml` looks like this:

```yaml
language: ruby
rvm:
- 2.6.3

branches:
  only:
  - travis
  except:
  - master

script:
  - bundle exec rspec

notifications:
  email: false
```

<details>
   <summary><sup>*</sup> Your project not in Ruby?</summary>
   
---

If your project is in a different language, no worries. Travis CI provides a large set of [language-specific guides for forming your `.travis.yml`](https://docs.travis-ci.com/user/language-specific/), [here](https://docs.travis-ci.com/user/language-specific/). 

For instance, here's the guide for [Javascript with Node](https://docs.travis-ci.com/user/languages/javascript-with-nodejs/).

---

</details>

Now that we've composed our `.travis.yml`, the next step is to add it to our project with a new commit:

```
git push
```

If you're committing to a branch on your project, you might want to change the push command to something like:

```
git push -u origin <my-new-branch>
```

But the point is the same, we're adding a new file, `.travis.yml` to our project.

And guess what?

That's all that's required to get Travis Ci to start creating builds of your project.

According to the Travis CI docs:

> *Travis only runs builds on the commits you push after you’ve added a .travis.yml file.*

But, glory is ours now.

Simply go back to [Travis CI (dot org)](https://travis-ci.org/) to see the first build on your project.

For us, that meant going [here](https://travis-ci.org/github/afinetooth/coveralls-demo-ruby). Specifically [https://travis-ci.org/github/afinetooth/coveralls-demo-ruby](https://travis-ci.org/github/afinetooth/coveralls-demo-ruby), where the format of your URL will be:

```
https://travis-ci.org/github/<your-github-username>/<your-github-repo>
```

Your first build will look something like this:

![travis-ci-repo-build-1.png](../media/media/travis-ci-repo-build-1.png)

Simply stated, a successful build; albeit, with not a lot going on.

So we're building at our CI.

Now, let's tell our CI to send its test results to Coveralls.


---

</details>

### 3. Add repo to Coveralls

<details>
   <summary>Do it.</summary>
   
---
   
WIP

---

</details>

### 4. Add `.coveralls.yml` to repo

<details>
   <summary>Do it.</summary>
   
---
   
WIPn

---

</details>

---

```
# To Do:
- [ ] Add Travis logo
- [ ] Add Coveralls logo
```
