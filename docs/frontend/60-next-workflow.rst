Next git flow
=============

Next branch should be used for anything not ready for master - master will be
promoted to alpha/beta/prod during normal release flow and any bigger 
changes/experimental features should be tested in next first, unless they are
ready for release or only requires minor testing.

Create regular pull request for master
--------------------------------------
This is done according to normal git flow.

Make sure next is rebased on master
----------------------------------------------
Visit `next <https://github.com/Neovici/cosmoz-frontend/tree/next>`_
on GitHub to check the current status.

It should say “This branch is X commits ahead of master.” and not anything about
being behind master.

If it is behind master, do the following::

	git checkout next
	git rebase master
	git push --force-with-lease

A reset of next might be needed if the rebase fails.

Create pull request for next
----------------------------
Head to https://github.com/Neovici/cosmoz-frontend/compare/next...branchName to
create a new pull request.

Reference the original pull request in the new pull request - add
``OPR: #prNumber`` at the end of the message.

Assign next pull request to testing
-----------------------------------
The testing team reviews the pull request and gives feedback.

Testing team review work procedure
----------------------------------
* Merge the pull request to next.
* Test the changes in the pull request.
* Give feedback on the pull request.

Additional fixes through pull requests
--------------------------------------
* Push to existing pull request
* Create a new pull request for next, assign it to testing or merge.

	* Reference original pull request, ``OPR: #prNumber``.

When testing approves the change, merge the original pull request to master
---------------------------------------------------------------------------
* Make sure no additional commits are present in the original pull request
  that has not been pull requested, merged and tested in next.

If needed: Reset next
---------------------
Do the following to reset next::

	git branch -D next
	git checkout -b next master
	# .. merge all needed branches
	git push --force-with-lease

Running experimental public components in next only
----------------------------------------------------
* Release a new minor-version of the component, for example 1.2.3 -> 1.3.3, 
  the three would signify which bugfixes that come along the version upgrade.
* Submit a pull request to frontend master to upgrade the component, see
  ``bower.json``.
* Submit the pull request and possibly merge or assign to testing team/person
  to next.
* Any additional fixes needed will become bugfix releases for the component, for
  example 1.3.0 -> 1.3.1.
* Note that frontend next needs to be rebuilt after public component release.