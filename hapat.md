3 Physical replication: a reminder

3.1 Introduction
  - Patroni is based on PostgreSQL physical replication
  - high availability involves technical teams
  - technical teams must understand the mechanics

Patroni sets up PostgreSQL's native physical replication to ensure data redundancy within the cluster. It's essential to grasp how this replication operates.
Indeed, since Patroni is designed to optimize availability, the administrator must be able to react quickly and identify the causes of a replication incident or quandary,
and recognize how to reintegrate a replicated node, etc., without creating an overload. And all of this, certainly, without creating an over-incident.

3.1.1 Overview
  - establishing physical replication
  - promotion
  - return to stable state

3.2 Establishing streaming replication
  - streaming replication
  - a process on the primary server talks to a process on the secondary server
    - resulting in lower lag
  - asynchronous or synchronous
  - cascade

The secondary PostgreSQL server launches a process called walreceiver, whose purpose is to connect to the primary server and wait for replication changes.
The walreceiver therefore needs to connect to the primary PostgreSQL server. The latter must be
formed to accept this connection. When accepted by the primary server, the PostgreSQL on the primary server launches a new process, called walsender. The purpose of this
to send replication data to the secondary server. Replication data is
activity and certain configuration parameters.
This method enables replication closer to the primary server than log shipping. You can even
even set up a synchronous mode: a client on the primary server doesn't take over until its modifications
changes are saved on the primary server and on the synchronous secondary server.
server. This is done when the transaction is validated, either implicitly or with a COMMIT .
Finally, cascade replication enables one secondary to provide replication information to
another secondary, thus relieving the primary server of a certain amount of work and reducing the
network bandwidth used by the primary server.
