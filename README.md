# MaryJS-Bitcoin

MaryJS-Bitcoin is a mobile-first Point-of-Sale module for the Mary Jane Operating System that merchants can use to accept Bitcoin payments instead of cash payments.

# How it Works

* Users are responsible for providing the receiving addresses managed with whatever wallet is preferred, so MaryJS never stores any bitcoins.
* Users create an account and configure some basic parameters for the storefront like a name, logo, and bitcoin receiving address
* Users set an exchange rate to be used to convert from the local currency to bitcoin
* MaryJS creates a custom screen that users can bring up on a mobile device to generate payment requests
* Users enter a sale amount in the local currency and MaryJS converts it to bitcoin using the chosen exchange rate
* MaryJS creates a QR code for the payment request with the receiving address and the sale amount encoded
* MaryJS listens for transactions on the Bitcoin network and displays a notification when the requested amount is received at the receiving address
* The details of the transaction and the exchange rate used at the time of sale are recorded and made available in a convenient report

# Technical Details

The module is developed to run independently or within MaryJS OS, and is written in Coffeescript using NodeJS, Angular, and jQuery. Account details and transaction data are stored in a Redis database or Firebase. 

MaryJS-Bitcoin uses the websocket payment notification API from http://blockchain.info/api/api_websocket to listen for and display payment notifications in real time. The bitcoin exchange rates are fetched from http://bitcoinaverage.com

# Installation

Install nodeJS (http://nodejs.org/) and redis (http://redis.io/) then:

    $ git clone https://github.com/BeardandFedora/MaryJS-Bitcoin
    $ cd MaryJS
    $ npm install  
    $ ./fetch_rates.sh
    $ coffee app

Now the app should be runnning at http://localhost:3000/

# Install as a Module in MarySJ

From inside your MaryJS application folder, follow these quick instructions:

	$ cd apps
    $ git clone https://github.com/BeardandFedora/MaryJS-Bitcoin
    $ cd MaryJS
    $ npm install  
    $ ./fetch_rates.sh
    $ grunt install 

Now that the app is installed as a module and the rates have been downloaded, you are ready to go.

# Contributing to MaryJS

Please take a moment to review [this document](CONTRIBUTING.md) ([CONTRIBUTING.md](CONTRIBUTING.md)) in order to make the contribution
process easy and effective for everyone involved.

Following these guidelines helps to communicate that you respect the time of
the developers managing and developing this open source project. In return,
they should reciprocate that respect in addressing your issue or assessing
patches and features.


## Using the issue tracker

The issue tracker is the preferred channel for [bug reports](#bugs),
[features requests](#features) and [submitting pull
requests](#pull-requests), but please respect the following restrictions:

* Please **do not** use the issue tracker for personal support requests.

* Please **do not** derail or troll issues. Keep the discussion on topic and
  respect the opinions of others.


<a name="bugs"></a>
## Bug reports

A bug is a _demonstrable problem_ that is caused by the code in the repository.
Good bug reports are extremely helpful - thank you!

Guidelines for bug reports:

1. **Use the GitHub issue search** &mdash; check if the issue has already been
   reported.

2. **Check if the issue has been fixed** &mdash; try to reproduce it using the
   latest `master` or development branch in the repository.

3. **Isolate the problem to MaryJS** &mdash; make sure that the code in the MaryJS
repository is _definitely_ responsible for the issue. Switch to a core WordPress
theme (such as Twenty Thirteen) to confirm problems before reporting an issue.
Make sure you have reproduced the bug with all plugins disabled. Any issues
related to HTML5 Boilerplate or Bootstrap should be reported to their respected
repositories and follow their contributing guidelines.

A good bug report shouldn't leave others needing to chase you up for more
information. Please try to be as detailed as possible in your report.


<a name="features"></a>
## Feature requests

Feature requests are welcome. But take a moment to find out whether your idea
fits with the scope and aims of MaryJS. It's up to *you* to make a strong
case to convince the MaryJS developers of the merits of this feature. Please
provide as much detail and context as possible.


<a name="pull-requests"></a>
## Pull requests

Good pull requests - patches, improvements, new features - are a fantastic
help. They should remain focused in scope and avoid containing unrelated
commits.

**Please ask first** before embarking on any significant pull request (e.g.
implementing features, refactoring code), otherwise you risk spending a lot of
time working on something that the developers might not want to merge into MaryJS.

Please adhere to the coding conventions used throughout the project (indentation,
comments, etc.).

Adhering to the following this process is the best way to get your work
included in MaryJS:

1. [Fork](http://help.github.com/fork-a-repo/) MaryJS, clone your fork,
   and configure the remotes:

   ```bash
   # Clone your fork of the repo into the current directory
   git clone https://github.com/<your-username>/<repo-name>
   # Navigate to the newly cloned directory
   cd <repo-name>
   # Assign the original repo to a remote called "upstream"
   git remote add upstream https://github.com/<upsteam-owner>/<repo-name>
   ```

2. If you cloned a while ago, get the latest changes from upstream:

   ```bash
   git checkout <dev-branch>
   git pull upstream <dev-branch>
   ```

3. Create a new topic branch (off the main project development branch) to
   contain your feature, change, or fix:

   ```bash
   git checkout -b <topic-branch-name>
   ```

4. Commit your changes in logical chunks. Please adhere to these [git commit
   message guidelines](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
   or your code is unlikely be merged into the main project. Use Git's
   [interactive rebase](https://help.github.com/articles/interactive-rebase)
   feature to tidy up your commits before making them public.

5. Locally merge (or rebase) the upstream development branch into your topic branch:

   ```bash
   git pull [--rebase] upstream <dev-branch>
   ```

6. Push your topic branch up to your fork:

   ```bash
   git push origin <topic-branch-name>
   ```

10. [Open a Pull Request](https://help.github.com/articles/using-pull-requests/)
    with a clear title and description.