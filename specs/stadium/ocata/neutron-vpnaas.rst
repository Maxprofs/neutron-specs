..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

========================
Neutron-vpnaas Scorecard
========================

Neutron integration
-------------------

.. _N0:

* N0. Does the project use the Neutron REST API or relies on proprietary backends?

  Neutron-vpnaas implements its own set of Neutron API extensions on top of
  the Neutron core framework and it does so by using the service plugin model.
  The API exposed has open source implementations, and it provides a pluggable
  mechanism for proprietary backends.

.. _N1:

* N1. Does the project integrate/use neutron-lib?

  Yes. The migration report shows that there are currently ~600 total imports.
  Neutron is imported ~150 times and Neutron-lib only ~15 times, for a migration
  percentage of 10.0500%

.. _N2:

* N2. Do project members actively contribute to help neutron-lib achieve its
  goal?

  None of the project core members have merged anything meaningful into neutron-lib
  (source: https://review.openstack.org/#/q/project:openstack/neutron-lib+status:merged,75).

.. _N3:

* N3. Do project members collaborate with the core team to enable subprojects
  to loosely integrate with the Neutron core platform by helping with the definition
  of modular interfaces?

  No.

.. _N4:

* N4. How does the project provide networking services? Does it use modular interfaces
  as provided by the core platform?

  Yes, for the most part, but as far as the agent side is concerned, the project relies
  on the use of a VPN agent that specializes the base L3 agent, this is prone to breakage,
  and leads to deployment complications when VPN and L3 services are deployed together.

  * https://github.com/openstack/neutron-vpnaas/blob/master/neutron_vpnaas/services/vpn/agent.py#L46
  * http://logs.openstack.org/64/385664/1/check/gate-neutron-vpnaas-dsvm-api-nv/a2f4f78/logs/screen-neutron-vpnaas.txt.gz

.. _N5:

* N5. If the project provides new API extensions, have API extensions been discussed
  and accepted by the Neutron drivers team? Please provide links to API specs, if
  required.

  The vpnaas API has been widely discussed and accepted.


Documentation
-------------

.. _D1:

* D1. Does the project have a doc tox target, functional and continuously
  working? Provide proof (links to logs.openstack.org).

  Yes.

  * https://github.com/openstack/neutron-vpnaas/blob/master/tox.ini

.. _D2:

* D2. If the project provide API extensions, does the project have an
  api-ref tox target, functional and continously working? Provide proof
  (links to logs.openstack.org).

  There is an API reference but no-one has confirmed its accuracy at the
  time of writing.

  * http://developer.openstack.org/api-ref/networking/
  * https://github.com/openstack/neutron-lib/blob/master/api-ref/source/v2/vpnaas.inc

.. _D3:

* D3. Does the project have a releasenotes tox target, functional and
  continously working? Provide proof.

  Yes.

  * https://github.com/openstack/neutron-vpnaas/blob/master/tox.ini
  * http://docs.openstack.org/releasenotes/neutron-vpnaas/

.. _D4:

* D4. Describe the types of documentation available: developer, end user,
  administrator, deployer.

  Developer documentation is sparse, user documentation is virtually non-existent.

  * http://docs.openstack.org/developer/neutron-vpnaas/
  * http://docs.openstack.org/mitaka/networking-guide/adv-config-vpnaas.html


Continuous Integration
----------------------

.. _C1:

* C1. Does the project have a Grafana dashboard showing historical trends of
  all the jobs available? Provide proof (links to grafana.openstack.org).

  No.

.. _C2:

* C2. Does the project have CI for unit coverage? Provide proof (links to
  logs.openstack.org)

  Yes.

  * http://status.openstack.org/openstack-health/#/g/project/openstack~2Fneutron-vpnaas

.. _C3:

* C3. Does the project have CI for functional coverage? If so, does it include
  DB migration and sync validation?

  Yes.

  * http://status.openstack.org/openstack-health/#/job/gate-neutron-vpnaas-dsvm-functional

.. _C4:

* C4. Does the project have CI for fullstack coverage?

  No.

.. _C5:

* C5. Does the project have CI for Tempest coverage? If so, specify nature
  (API and/or Scenario).

  Latest Bot proposal shows a `mixed picture <https://review.openstack.org/#/c/377475/>`_,
  API coverage is non-voting.

.. _C6:

* C6. Does the project require CI for Grenade coverage?

  Yes. But it has none.

.. _C7:

* C7. Does the project provide multinode CI?

  No.


.. _C8:

* C8. Does the project support Python 3.x? Provide proof.

  Yes.


Release footprint
-----------------

.. _R1:

* R1. Does the project adopt semver?

  Yes.

.. _R2:

* R2. Does the project have release deliverables? Provide proof as available
  in the `release repo <http://git.openstack.org/cgit/openstack/releases/tree/>`_.

  Yes, the release is responsibility of the neutron-release team.

.. _R3:

* R3. Does the project use upper-constraints?

  Yes.

  * https://github.com/openstack/neutron-vpnaas/blob/master/tox.ini#L10

.. _R4:

* Does the project integrate with OpenStack Proposal Bot for requirements updates?

  * Yes.

  * https://github.com/openstack/requirements/commit/1d545edbebfff2e8983d6cab24a92c32636dd6bf


Stable backports
----------------

.. _S1:

* S1. Does the project have stable branches and/or tags? Provide history of
  backports.

  Yes, stable maintainance is responsibility of the neutron-stable team.


Client library
--------------

.. _L1:

* L1. If the project requires a client library, how does it implement CLI and
  API bindings?

  There are Neutron CLI and API bindings, but none for OSC.


Scorecard
---------

+---------------+
| Scorecard     |
+===============+
| N0_ |    Y    |
+---------------+
| N1_ |    Y    |
+---------------+
| N2_ |    N    |
+---------------+
| N3_ |    N    |
+---------------+
| N4_ |    N    |
+---------------+
| N5_ |    Y    |
+---------------+
| D1_ |    Y    |
+---------------+
| D2_ |    N    |
+---------------+
| D3_ |    Y    |
+---------------+
| D4_ |    N    |
+---------------+
| C1_ |    N    |
+---------------+
| C2_ |    Y    |
+---------------+
| C3_ |    Y    |
+---------------+
| C4_ |    N    |
+---------------+
| C5_ |    N    |
+---------------+
| C6_ |    N    |
+---------------+
| C7_ |    N    |
+---------------+
| C8_ |    Y    |
+---------------+
| R1_ |    Y    |
+---------------+
| R2_ |    Y    |
+---------------+
| R3_ |    Y    |
+---------------+
| R4_ |    Y    |
+---------------+
| S1_ |    Y    |
+-----+---------+
| L1_ |    N    |
+-----+---------+


Final remarks
-------------

At the time of writing the project scores positively in about half of the
criteria. The neutron-vpnaas project has been in the doldrums for quite a
while and the release notes show it. Closing the gap on all the remaining
unmet criteria in time for Ocata-1 (Nov 14 2016) knowing the level of
commitment required and lack of resources available makes it clear that
this project is ready to be left to its own destiny.
