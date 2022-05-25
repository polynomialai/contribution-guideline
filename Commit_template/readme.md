
Source Control Commit Guidelines
================================

**Table of Contents:**

- [Source Control Commit Guidelines](#source-control-commit-guidelines)
  - [Prefer Atomic Commits](#prefer-atomic-commits)
  - [Commit Message Guidelines](#commit-message-guidelines)
    - [The Subject](#the-subject)
    - [The Message Body](#the-message-body)
    - [Reference Issue Numbers](#reference-issue-numbers)
    - [On Cherry-Picked Commits](#on-cherry-picked-commits)
  - [Revise Your Commits Before Submitting a PR](#revise-your-commits-before-submitting-a-pr)

Prefer Atomic Commits
---------------------

In general, the smaller the commit, the better. We prefer [atomic commits](https://en.wikipedia.org/wiki/Atomic_commit), which apply a distinct and related set of changes in a single action.

What does this mean in practical terms?

1.  All changes in a commit should be related.
    1.  Don’t combine changes that address different problems into a single commit.
2.  All changes in a commit should address a single aspect of a problem or change.
    1.  Don’t be afraid to break up a new feature, bug fix, or refactoring effort into multiple distinct changes.
    2.  This will help you keep track of what works and what doesn’t: if there’s a problem, you can always revert back to the last known good state. If you wait too long between commits, you may lose a lot of work or spend too long finding the source of the problem.
3.  Prefer _small_ commits to _large_ commits.
    1.  This helps reviewers by allowing them to focus on a small set of related changes.
    2.  This helps future debugging efforts by increasing the probability that a `git bisect` operation will quickly identify the source of the problem.



Commit Message Guidelines
-------------------------



    50-char-ish "subject" which summarizes the change
    
    After the first line, include additional explanatory text. Include
    one blank line in between the summary and the body. Various tools
    like git log, git shortlog, and git rebase get confused if the two
    sections run together.
    
    You can also include bullet points:
    * A
    * B
    * C
    
    Reference issues at the bottom, like this:
    
    Fixes #102
    Relates to #100, #8

### The Subject

Treat the first line of a commit message like an email subject line.

You can find the commit subject guidelines at [Subject Guidelines](Commit_template/../commit_guidelines.md)

We recommend a maximum length of 50 characters because it works best with git’s command line tools.


Another way to look at it is to have your subject line complete the following sentence:

> If applied, this commit will _\[subject line here\]_.

We don’t worry about manual line breaks in our commit message bodies. Text wrapping works well in modern tools.

### The Message Body

Please separate the body from the subject with a blank line.

Most importantly, the commit message body should be used to explain _what_ you are doing and _why_ you did it that way, rather than _how_ you did it. The code itself serves to explain the _how_. Focus on side effects, [compatibility](https://embeddedartistry.com/fieldmanual-terms/compatibility/) changes, or other consequences that are not immediately obvious from reviewing the code. Also include any important factors that helped you arrive at your particular approach.

Not all commit messages require both a subject and a body. You can include only a subject if it is sufficient for a given commit.

### Reference Issue Numbers

When working with GitHub projects, reference relevant issue numbers in your commit message body.

You can have a commit automatically close an issue when it is merged to `master` by saying something like the following in your message body:

    Fixes #123
    Fixes: #123
    Resolves: #123

You can also reference issues in other repositories by adding a prefix for `organization/repository`:

    Fixes octo-org/octo-repo#100

> Note: The full list of keywords that will close an issue is found in [the GitHub documentation](https://help.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue).

If other issues or PRs are related to this commit, but it doesn’t address the problem, you can include the issue/PR number without using a keyword like “fixes” or “resolves”. This will link the commit and the issue in GitHub’s web interface.

### On Cherry-Picked Commits

Sometimes, we cherry-pick changes from one branch to another. We recommend [using the `-x` flag](https://embeddedartistry.com/blog/2016/10/19/git-cherry-pick-recommendations/) with `git cherry-pick`, which references the original commit [ID](https://embeddedartistry.com/fieldmanual-terms/industrial-design/).

For more information, see [Git Cherry-pick Recommendations](https://embeddedartistry.com/blog/2016/10/19/git-cherry-pick-recommendations/).

Revise Your Commits Before Submitting a PR
------------------------------------------

While you’re working on a problem on your own branch, don’t worry about getting these commit details perfect. Instead, clean up your branch before you submit a PR. You can perform a [git rebase](https://git-scm.com/docs/git-rebase) to squash commits, amend commit messages, and more.

We often use a visual tool, such as [Sourcetree](https://www.sourcetreeapp.com/), for complex rebase process.
