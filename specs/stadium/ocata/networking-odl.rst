..
 This work is licensed under a Creative Commons Attribution 3.0 Unported
 License.

 http://creativecommons.org/licenses/by/3.0/legalcode

========================
Networking-odl Scorecard
========================

Neutron integration
-------------------

.. _N0:

* N0. Does the project use the Neutron REST API or relies on proprietary backends?

No, the project maps the various Neutron APIs on top of the OpenDayLight SDN controller.

.. _N1:

* N1. Does the project integrate/use neutron-lib?

  Yes. Roughly only 10% of the imports have been migrated over.

.. _N2:

* N2. Do project members actively contribute to help neutron-lib achieve its
  goal?

  No. There is no evidence of that.

.. _N3:

* N3. Do project members collaborate with the core team to enable subprojects
  to loosely integrate with the Neutron core platform by helping with the definition
  of modular interfaces?

  There is some evidence of that, especially in relation to how the registry component
  has been defined.

.. _N4:

* N4. How does the project provide networking services? Does it use modular interfaces
  as provided by the core platform?

  Yes.

.. _N5:

* N5. If the project provides new API extensions, have API extensions been discussed
  and accepted by the Neutron drivers team? Please provide links to API specs, if
  required.

  The project currently provides driver for various APIs like SFC, L2GW, QoS, etc.
  Some of these APIs need closer scrutiny by the neutron drivers team. Please,
  read assessment for the relevant projects.


Documentation
-------------

.. _D1:

* D1. Does the project have a doc tox target, functional and continuously
  working? Provide proof (links to logs.openstack.org).

  Yes.

  * http://docs.openstack.org/developer/networking-odl/

.. _D2:

* D2. If the project provide API extensions, does the project have an
  api-ref tox target, functional and continously working? Provide proof
  (links to logs.openstack.org).

  The project does not propose new APIs.

.. _D3:

* D3. Does the project have a releasenotes tox target, functional and
  continously working? Provide proof.

  The target seems set up but no release notes are available.

  * https://github.com/openstack/networking-odl/tree/master/releasenotes/notes
  * http://docs.openstack.org/releasenotes/networking-odl/

.. _D4:

* D4. Describe the types of documentation available: developer, end user,
  administrator, deployer.

  The documentation is available but content is bare bone. Host Configuration
  is all there seems to be available. If OpenDaylight-hosted content is available,
  this should at least be referenced.

  * http://docs.openstack.org/developer/networking-odl/devref/hostconfig.html


Continuous Integration
----------------------

.. _C1:

* C1. Does the project have a Grafana dashboard showing historical trends of
  all the jobs available? Provide proof (links to grafana.openstack.org).

  Yes.

  * http://grafana.openstack.org/dashboard/db/networking-odl-failure-rate

.. _C2:

* C2. Does the project have CI for unit coverage? Provide proof (links to
  logs.openstack.org)

  Yes.

  * http://logs.openstack.org/94/376994/1/check/gate-networking-odl-python27-ubuntu-xenial/b4d0ae2/

.. _C3:

* C3. Does the project have CI for functional coverage? If so, does it include
  DB migration and sync validation?

  No. There seems there is no DB migration and sync validation as the project
  introduces its own data models. `Review <https://review.openstack.org/#/c/384509/>`_
  is eloquent.

.. _C4:

* C4. Does the project have CI for fullstack coverage?

  No.

.. _C5:

* C5. Does the project have CI for Tempest coverage? If so, specify nature
  (API and/or Scenario).

  Yes, voting, though exercising only a subset of API tests and none of the
  scenario tests affecting networking.

  * https://review.openstack.org/#/c/383124/

.. _C6:

* C6. How does a project validate upgrades on a continuous basis? Does
  the project require or support CI for Grenade coverage?

  The plan is to require it in early Ocata for openstack upgrade. Upgrading
  CI runs against each supported ODL releases (berrylium, boron and carbon)
  in order to guarantee the compatibility between neutron master vs ODL
  versions. On the other hand, neutron stables + ODL master is tested by
  opendaylight test infra.

.. _C7:

* C7. Does the project provide multinode CI?

  No.

.. _C8:

* C8. Does the project support Python 3.x? Provide proof.

  Yes.

  * http://logs.openstack.org/94/376994/1/check/gate-networking-odl-python35/4c26a70/testr_results.html.gz


Release footprint
-----------------

.. _R1:

* R1. Does the project adopt semver?

  Yes.

.. _R2:

* R2. Does the project have release deliverables? Provide proof as available
  in the `release repo <http://git.openstack.org/cgit/openstack/releases/tree/>`_.

  Yes.

  * https://github.com/openstack/releases/blob/master/deliverables/_independent/networking-odl.yaml

.. _R3:

* R3. Does the project use upper-constraints?

  Yes.

  * https://github.com/openstack/networking-odl/blob/master/tox.ini#L11

.. _R4:

* Does the project integrate with OpenStack Proposal Bot for requirements updates?

  Yes.

  * https://github.com/openstack/requirements/commit/87f95992bf7b419b71faa52590edef8b7ee37f1a


Stable backports
----------------

.. _S1:

* S1. Does the project have stable branches and/or tags? Provide history of
  backports.

  The stable backports have been historically managed by the Neutron team.


Client library
--------------

.. _L1:

* L1. If the project requires a client library, how does it implement CLI and
  API bindings?

  It does not seem like client extensions are required.


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
| N3_ |    Y    |
+---------------+
| N4_ |    Y    |
+---------------+
| N5_ |    Y    |
+---------------+
| D1_ |    Y    |
+---------------+
| D2_ |    Y    |
+---------------+
| D3_ |    Y    |
+---------------+
| D4_ |    N    |
+---------------+
| C1_ |    Y    |
+---------------+
| C2_ |    Y    |
+---------------+
| C3_ |    N    |
+---------------+
| C4_ |    N    |
+---------------+
| C5_ |    Y    |
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
| L1_ |    Y    |
+-----+---------+

Final remarks: better coverage and more exhaustive documentation are the gaps
identified with this project.
