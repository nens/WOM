Workflow
========

**Don't make me think:** this is how we do develop release and manage software.

**Development:**

* `Design <design>`_
* `New feature <new_feature>`_
* `Definition of done (DOD) <definition_of_done_(DOD)>`_
* `Migrations <migrations>`_
* `Bug fixes <bug_fixes>`_
* `Deploy <deploy>`_
* `Documentation <documentation>`_

**DevOps:**

* `server_setup`_
* `provisioning`_
* `deployment`_
* `package_management`_
* `virtual_machine`_
* `continuous_integration`_


Design
------

Before you start developing on a feature, make sure it is designed. If you are working alone or in a small team, design can be implicit based on common context and knowledge. If you are working in a team of more than 3 people, implicit common context and knowledge are very difficult to maintain. In that case it is almost always better to eplicitly design a feature and share it.

Large chunks of new functionality, or new concepts can be designed as a Request For Change (RFC). RFC's are documented as Github issues with a label `RFC`. From an RFC you can design bite size new features as user stories, issues, tickets, whatever. A user story is a ticket in the backlog (Trello, physical board) with a title, estimate and possibly a reference to an RFC and a contact person (CP).


.. _new_feature:

New feature
-----------

Check the Todo column of the backlog (whiteboard, Trello, your head) and select a ticket you'd like to develop. Check the DOD for TODO >> Doing. If something is not clear, discuss with the contact person. If they are clear and you agree with the estimate, move the card to **Doing** and start developing::

    git checkout master
    git checkout -b <yourname>_<feature_name>

When you are done developing (including tests and documentation):

* Update CHANGES.rst
* Merge with latest master::

    git pull origin master

* Push the code to github::

    git push origin <yourname>_<feature_name>

* Open a pull request to master
* Ask someone to review your code
* Merge pull request with master
* Delete feature branch::
    
    git branch -d <yourname>_<feature_name>

Move your ticket to **Done**.


.. _DOD:

Definition of done (DOD)
------------------------

Checklist to make sure that **quality and documentation** are **built in**. Steps are partly based on `requirements of maintenance <https://docs.google.com/a/nelen-schuurmans.nl/document/d/1qHP96AAst8tRvTV5z1MDUx4Tl1Xk0zmU-r22U4-N_KA/edit?usp=sharing>`_.

.. _DOD_todo_doing:

**Todo >> Doing:**

* Open a Pull Request on Github.
* Write a spec in the PR (check RFC).
* Ask feedback on the spec.

.. _DOD_rft_done:

**Doing >> done:**

* Entry in changelog.
* Check if feature is described in concepts of developer docs.
* Check code syntax, bugs, structure.
* Check code documentation (python Google style docstring, javascript jsdoc).
* Check tests for feature (unit / integration tests).
* Check if feature complies with user story.
* Make (a) new ticket(s) for possible new issues / improvements.

.. _DOD_sprint:

**Sprint done:**

Each sprint a person is appointed who is responsible for successful end of the sprint (runs this checklist).

* Check open features / PR 2 days before sprint end.
* All PR reviewed and merged.
* Architecture documentation updated.
* Troubleshoot guide updated.
* Features are released to staging server on the day before demo.
* Features are demo-ed to Product Owner and users.
* Feedback from Product Owner is processed.
* Retrospective meeting.

**Future candidates:**

* Performance testing passes benchmark.
* Code coverage unit test at X%.

.. _DOD_release:

**Release done:**

* User acceptance tests pass.
* User manual updated.
* Disaster recovery plan updated.
* Stress testing.

    
Migrations
----------

Be careful with migrations. Work on migrations with::

    bin/django schemamigration --auto
    bin/django migrate

Work on your code but **don't commit the migration yet!**. When you update your model::

    bin/django schemamigration --auto --update
    bin/django migrate

Before you commit migrations, pull the master branch, notify your team members, make the migration, push to github and make a pull request to ``master``.

    
.. _bug_fixes:

Bug fixes
---------

Overview
^^^^^^^^^

* Check which version in running on production / staging: 3.1.3
* ``git checkout 3.1.3`` (you are now in detached mode)
* ``git checkout -b fixes_3.1`` (you are now a fixes branch)
* ``git checkout -b arjen_useful_bugfix_name``
* fix bug and make PR to fixes branch new release
* merge fix to fixes branch, release and deploy
* merge fixes branch to master


Step by step
^^^^^^^^^^^^

Create new fixes branch from ``tag`` and create new bugfix branch::
    
    git checkout <tag>
    git checkout -b <fixes_branch_name>
    git push origin <fixes_branch_name>
    git checkout -b <username>_<useful_bugfix_name>

Where <tag> is tagname eg ``1.4.4``. Write unit test for bug, fix bug, document (including CHANGES.rst), commit, review then **release**, then merge with master::

    git push origin <bugfix_branch_name>

* Open pull request to ``<fixes_branch_name>``.
* Ask someone to review your code.
* When ok, `release`_ bugfix **from fixes branch, make sure to only update the ``patch`` number**.
* Deploy to production.
* Merge fixes branch with master.

Delete bugfix branch::

    git branch -d <username>_<useful_bugfix_name>

Optionally you can choose to keep the fixes branch alive or delete it. After a feature release it's usually practical to keep a fixes branch around for 1 or 2 sprints.

        
.. _release:

Release
-------

To release *new features* to staging or production, first make a release::

    git checkout master
    git pull origin master

Pin all third party packages in buildout to required version. Remember to set the proper versions for packages that are in autocheckout in development.cfg.

Make a release with `fullrelease`::

    bin/fullrelease

**NOTE:** 

* When you do a regular release, make sure you update the ``major`` or ``minor`` version number, not the ``patch`` number.

* When you do a fixes release, make sure you update the ``patch`` number, not the ``major`` or ``minor`` version number.

If you don't have `fullrelease`, make a release by hand::
    
    <update CHANGES.rst>
    git tag -a <version.sub_version.patch> -m "<tag message>"
    git push origin staging --tags

To check which tag you are on::

    git describe --tags


Unit tests
----------

TODO

Documentation
-------------

Documentation can be done in ReStructuredText or Markdown

Project

* README.rst
* CHANGES.rst

Project documentation is processed with `Sphinx`. Comes with buildout:: 

    bin/sphinx

Python documentation with Google style docstrings.

Javascript documentation with JSDoc. Install jsdoc and run::
    
    jsdoc -c jsdoc-conf.json -d doc
    
For example see https://github.com/nens/lizard-client


.. _server_setup:

Server setup
------------

There are two more or less parallel models for the software development process:

* Development Integration Staging Production (DISP)
* Development Test Acceptance Production (DTAP, (OTAP in Dutch))

We use the DISP terminology.

* **Development** is your own machine or virtual machine, do whatever you want, configure as you like. It's not a bad idea though to have virutal machine on your local box that is configured as much as possible like the production environment. You probably run the unstable HEAD of your feature branch.
* **Integration** is an internal server used to integrate features. Integration is running the unstable HEAD of the **master** branch.
* **Staging** is an external accessible server with only released (pinned) packages, used to do acceptance tests. Staging is running a beta version **x_0by** of the **x_0** branch.
* **Production** is the production server. It runs a stable release.

In SCM this looks like this::

    master
      |
      |   {user}_{feature}
      |----------
      |         |
      |     (features)
      |         |
      |   (pull request)
      |         |
      |<---------
      |
     1.0
      |
      |     {user}_{bugfix}
     1.1--------
      |         |
      |     (bugfix)
      |         |
      |   (pull request)
      |         |
      |     (release)
      |         |
      |       1.1.1
      |         |
      |<---------
      |

In the above example developers build features in feature branches from the master branch.
After a pull request these are merged back into the master branch.
When development is ready, features are released. The release is tagged 1.0b1 and deployed to staging environment.
When customer accepts the beta on staging, it is released as 1.0.
A bug on production is fixed on a bug fix branch tested and released as 1.0.1, then deployed to production and merge to master.

Apart from development, it's usually not a good idea to login as a user to one of the other servers. If you have to do that there is probably a bug in your `provisioning`_ or `deployment`_ setup.


.. _provisioning:

Provisioning
------------

Provisioning is server setup that is done only once.

Provisioning is done with `ansible`

Provisioning for integration, staging and production is done with an ansible script. **Integration**::

    ansible-playbook -i deploy/local --limit=nxt-integration -K deploy/provision.yml

**Staging**::

    ansible-playbook -i deploy/local --limit=nxt-staging -K deploy/provision.yml 

**Production**::

    ansible-playbook -i deploy/local --limit=nxt-production -K deploy/provision.yml 


.. _deployment:

Deployment
----------

**NOTE:** Make sure you have setup ssh-config properly so you use the right credentials for logging on to the server.

Deployment is publishing your application to the server. Deployment can be done many times. If you have a task in deployment which is done only once, that could be a sign that that task belongs to provisioning.

Deployment to **integration** is done automatically via the integration server (http://buildbot.lizardsystem.nl/jenkins/view/Lizard%20NXT/).

Deploy  to **staging** (example for lizard-nxt)::

    ansible-playbook -i deploy/local --limit=nxt-staging -K deploy/deploy.yml --extra-vars "branch=<tag_name> client_version=<tag_name>"

where `tag_name` is name of the tag you want to deploy.

Deploy to **production**:

    ansible-playbook -i deploy/local --limit=nxt-production -K deploy/deploy.yml --extra-vars "branch=<tag_name> client_version=<tag_name>"

**NOTE:** lizard-nxt versions higher than 1.1.0 support release of only the client. If you only want to release the client, add `client_only=true` to the `--extra-vars` command line option like so, since that release you also specifically have to specify the client_version you want to release. Lizar-client is not a dependency of lizard-nxt anymore::

    ansible-playbook -i deploy/local --limit=nxt-staging -K deploy/deploy.yml --extra-vars "branch=<tag_name> client_version=<tag_name> client_only=true"

If you don't want to use ssh-keys install sshpass and tell ansible to ask for your password::

    sudo apt-get install sshpass

    ansible-playbook -i deploy/local --limit=nxt-staging -K -u <your.username> -k deploy/deploy.yml --extra-vars "branch=<branch_name>"


.. _package_management:

Package management
------------------

We use buildout for python package management, bower for javascript frontend packages and npm for node packages.


.. _continuous_integration:

Continuous integration
-----------------------

Continuous integration is done with Jenkins (http://buildbot.lizardsystem.nl/jenkins/view/Lizard%20NXT/).

Jenkins combines several build steps in an automated pipeline, triggered by a change on the integration branch on Github:

1. Checkout new code on build server and run tests.
2. If tests are successful, deploy code to integration server.
3. If deployment is successful, run acceptance tests.


.. _virtual_machine:

Virtual machine
---------------

`Vagrant <http://www.vagrantup.com>`_ with lxc.
