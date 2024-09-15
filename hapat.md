3 Physical replication: a reminder

3.1 Introduction
  - Patroni is based on PostgreSQL physical replication
  - high availability involves technical teams
  - technical teams must understand the mechanics

  Patroni sets up PostgreSQL's native physical replication to ensure data redundancy within the cluster. It's essential to grasp how this replication operates.
Indeed, since Patroni is designed to optimize availability, the administrator must be able to react quickly and identify the causes of a replication incident or quandary,
and recognize how to reintegrate a replicated node, etc., without creating an overload. And all of this, certainly, without creating an over-incident.
