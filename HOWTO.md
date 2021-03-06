How To
========

This document is meant to help our visitors
with our service interface.

Getting started
-----------------------

| Figure 1. Landing page | 
| ---- | 
| ![Landing page](/screenshots/main_page.png?raw=true) |

First, you see our landing page. You can scroll down to see some additional
information, if you want, but to use our project you need to press the green 
button in the middle of the screen.  

| Figure 2. GitHub authentication screen | 
| ---- | 
| ![GitHub authentication screen](/screenshots/github_auth.png?raw=true)  |

You'll be redirected to GitHub where you authenticate your GitHub account with
OAuth.
  
We do not access your GitHub password
and you can revoke our access at any time.

| Figure 3. Codestyles page | 
| ---- | 
| ![Codestyles page](/screenshots/first_time_in.png?raw=true)  |

After authenticating you are redirected to the Code Styles page, where you need
to add Code Style.

| Figure 4. Add codestyle popup | 
| ---- | 
| ![Add codestyle popup](/screenshots/getting_codestyle.png?raw=true)  |

Paste your repo address and name codestyle you're creating.

Hooray! You've added your first codestyle. Now you need to add
hook to the repository you want to manage. So we go to the Repos page.
Your repos will already be loaded there, but if no, press the refresh button
in the right bottom side of the screen.

| Figure 5. Repositories list | 
| ---- | 
| ![Repositories list](/screenshots/repo_list.png?raw=true)  |

Select the repo you want and press the tick in the popup near codestyle you
want to hook to the repo.

| Figure 6. Repo popup | 
| ---- | 
| ![Repo popup](/screenshots/setting_codestyle.png?raw=true)  |

Now webhook is set to your repository, and you can prove it if you go to Settings of 
your Repo on GitHub.

Congratulations! Wait for pull-requests to your project and our bot will comment all
you repo's codestyle violations.
