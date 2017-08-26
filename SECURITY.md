Security
========

This document is intended to help our customers'
security, risk, compliance, or developer teams
evaluate what we do with our customers' code and data.

Vulnerability Reporting
-----------------------

For security inquiries or vulnerability reports, please email
<>.
If you'd like, you can use our [PGP key] when reporting vulnerabilities.

[PGP key]: https://thoughtbot.com/thoughtbot.asc

thoughtbot
----------

What happens when you authenticate your GitHub account
------------------------------------------------------

CheckiePy uses Github OAuth to
authenticate your GitHub account and provide GitHub token.

[gh-oauth]: https://developer.github.com/v3/oauth/

Using OAuth2 means we do not access your GitHub password
and that you can revoke our access at any time.

Your GitHub token is needed in order to fetch file content, comments, repo
information and update Pull Request status. This token is encrypted and encoded 
and stored in our Postgres database in Docker container.


What happens when you enable CheckiePy on your GitHub repository
------------------------------------------------------------

When you click the "Connecnt" button in the Hound web interface
for one of your GitHub repositories,
we send your GitHub token from the web browser's session to our server.

We use your GitHub token to add the [@CheckiePyBot] GitHub user to your repository
via the [GitHub collaborator API][api1]. @CheckiePy will be added to a team that
has access to the enabled repository. If an existing team cannot be found, we'll
create a "Services" team with *push* access to the enabled repository. This is
necessary for @CheckiePy to see pull requests, make comments, and update pull
request statuses.

[@CheckiePyBot]: https://github.com/CheckiePyBot
[api1]: https://developer.github.com/v3/repos/collaborators/#add-collaborator

We also create a webhook on your repository via the [GitHub webhook API][api2].
This allows us to receive pull request notifications.

[api2]: https://developer.github.com/v3/repos/hooks/#create-a-hook

  
What happens when you teach codestyle on your repository
------------------------------------------------------

CheckiePy loads all the files in the repository and goes through all files
that repo contains, filling data about codestyle metrics.


What happens when we receive a pull request notification
--------------------------------------------------------

When you open a pull request on your GitHub repo,
or push a new commit to the branch for that pull request,
CheckiePy receives the payload.
This payload doesn't contain any code.
It contains metadata about the pull request such as repo, user, and commit.

The payload is stored on server, so we can check codestyle on it in a background job.

Using the information from the payload,
it makes a new HTTP request to GitHub's API to get
the pull request's patch and file contents.

We inspect codestyle from the repo
and pass inspections back up to our bot,
which uses the [GitHub commenting API][comment-api]
to comment about the inspections failed in the pull request.

[comment-api]: https://developer.github.com/v3/pulls/comments/


Third-party auditing
--------------------

We can't afford to hire a third party security company to audit CheckiePy,
but the codebase is open source.
We believe that transparency and this document can help keep CheckiePy
as secure as possible.
