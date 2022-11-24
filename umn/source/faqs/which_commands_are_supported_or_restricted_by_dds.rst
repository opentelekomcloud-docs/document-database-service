:original_name: dds_faq_0033.html

.. _dds_faq_0033:

Which Commands are Supported or Restricted by DDS?
==================================================

The following tables list the commands supported and restricted by DDS.

.. table:: **Table 1** Commands supported and restricted by DDS

   +------------------------------------+--------------------------+-------------------------+
   | Type                               | Supported Command        | Restricted Command      |
   +====================================+==========================+=========================+
   | Aggregates Commands                | aggregate                | mapReduce               |
   |                                    |                          |                         |
   |                                    | count                    |                         |
   |                                    |                          |                         |
   |                                    | distinct                 |                         |
   |                                    |                          |                         |
   |                                    | group                    |                         |
   +------------------------------------+--------------------------+-------------------------+
   | Geospatial Commands                | geoNear                  | geoSearch               |
   +------------------------------------+--------------------------+-------------------------+
   | Query and Write Operation Commands | find                     | getPrevError            |
   |                                    |                          |                         |
   |                                    | insert                   | eval                    |
   |                                    |                          |                         |
   |                                    | update                   | parallelCollectionScan  |
   |                                    |                          |                         |
   |                                    | delete                   |                         |
   |                                    |                          |                         |
   |                                    | findAndModify            |                         |
   |                                    |                          |                         |
   |                                    | getMore                  |                         |
   |                                    |                          |                         |
   |                                    | getLastError             |                         |
   |                                    |                          |                         |
   |                                    | resetError               |                         |
   +------------------------------------+--------------------------+-------------------------+
   | Query Plan Cache Commands          | planCacheListFilters     | ``-``                   |
   |                                    |                          |                         |
   |                                    | planCacheSetFilter       |                         |
   |                                    |                          |                         |
   |                                    | planCacheClearFilters    |                         |
   |                                    |                          |                         |
   |                                    | planCacheListQueryShapes |                         |
   |                                    |                          |                         |
   |                                    | planCacheListPlans       |                         |
   |                                    |                          |                         |
   |                                    | planCacheClear           |                         |
   +------------------------------------+--------------------------+-------------------------+
   | Authentication Commands            | logout                   | authSchemaUpgrade       |
   |                                    |                          |                         |
   |                                    | authenticate             | copydbgetnonce          |
   |                                    |                          |                         |
   |                                    | getnonce                 |                         |
   +------------------------------------+--------------------------+-------------------------+
   | User Management Commands           | createUser               | ``-``                   |
   |                                    |                          |                         |
   |                                    | updateUser               |                         |
   |                                    |                          |                         |
   |                                    | dropUser                 |                         |
   |                                    |                          |                         |
   |                                    | dropAllUsersFromDatabase |                         |
   |                                    |                          |                         |
   |                                    | grantRolesToUser         |                         |
   |                                    |                          |                         |
   |                                    | revokeRolesFromUser      |                         |
   |                                    |                          |                         |
   |                                    | usersInfo                |                         |
   +------------------------------------+--------------------------+-------------------------+
   | Role Management Commands           | invalidateUserCache      | ``-``                   |
   |                                    |                          |                         |
   |                                    | createRole               |                         |
   |                                    |                          |                         |
   |                                    | updateRole               |                         |
   |                                    |                          |                         |
   |                                    | dropRole                 |                         |
   |                                    |                          |                         |
   |                                    | dropAllRolesFromDatabase |                         |
   |                                    |                          |                         |
   |                                    | grantPrivilegesToRole    |                         |
   |                                    |                          |                         |
   |                                    | revokePrivilegesFromRole |                         |
   |                                    |                          |                         |
   |                                    | grantRolesToRole         |                         |
   |                                    |                          |                         |
   |                                    | revokeRolesFromRole      |                         |
   |                                    |                          |                         |
   |                                    | rolesInfo                |                         |
   +------------------------------------+--------------------------+-------------------------+
   | Replication Commands               | isMaster                 | replSetElect            |
   |                                    |                          |                         |
   |                                    |                          | replSetUpdatePosition   |
   |                                    |                          |                         |
   |                                    |                          | appendOplogNote         |
   |                                    |                          |                         |
   |                                    |                          | replSetFreeze           |
   |                                    |                          |                         |
   |                                    |                          | replSetGetStatus        |
   |                                    |                          |                         |
   |                                    |                          | replSetInitiate         |
   |                                    |                          |                         |
   |                                    |                          | replSetMaintenance      |
   |                                    |                          |                         |
   |                                    |                          | replSetReconfig         |
   |                                    |                          |                         |
   |                                    |                          | replSetStepDown         |
   |                                    |                          |                         |
   |                                    |                          | replSetSyncFrom         |
   |                                    |                          |                         |
   |                                    |                          | resync                  |
   |                                    |                          |                         |
   |                                    |                          | applyOps                |
   |                                    |                          |                         |
   |                                    |                          | replSetGetConfig        |
   +------------------------------------+--------------------------+-------------------------+
   | Sharding Commands                  | enableSharding           | flushRouterConfig       |
   |                                    |                          |                         |
   |                                    | getShardVersion          | addShard                |
   |                                    |                          |                         |
   |                                    | mergeChunks              | cleanupOrphaned         |
   |                                    |                          |                         |
   |                                    | shardCollection          | checkShardingIndex      |
   |                                    |                          |                         |
   |                                    | split                    | listShards              |
   |                                    |                          |                         |
   |                                    | splitChunk               | removeShard             |
   |                                    |                          |                         |
   |                                    | splitVector              | getShardMap             |
   |                                    |                          |                         |
   |                                    | moveChunk                | setShardVersion         |
   |                                    |                          |                         |
   |                                    | movePrimary              | shardingState           |
   |                                    |                          |                         |
   |                                    | isdbgrid                 | unsetSharding           |
   +------------------------------------+--------------------------+-------------------------+
   | Administration Commands            | renameCollection         | clone                   |
   |                                    |                          |                         |
   |                                    | dropDatabase             | cloneCollection         |
   |                                    |                          |                         |
   |                                    | listCollections          | clean                   |
   |                                    |                          |                         |
   |                                    | drop                     | connPoolSync            |
   |                                    |                          |                         |
   |                                    | create                   | compact                 |
   |                                    |                          |                         |
   |                                    | convertToCapped          | setParameter            |
   |                                    |                          |                         |
   |                                    | filemd5                  | repairDatabase          |
   |                                    |                          |                         |
   |                                    | createIndexes            | repairCursor            |
   |                                    |                          |                         |
   |                                    | listIndexes              | touch                   |
   |                                    |                          |                         |
   |                                    | dropIndexes              | shutdown                |
   |                                    |                          |                         |
   |                                    | fsync                    | cloneCollectionAsCapped |
   |                                    |                          |                         |
   |                                    | connectionStatus         | copydb                  |
   |                                    |                          |                         |
   |                                    | collMod                  | logRotate               |
   |                                    |                          |                         |
   |                                    | reIndex                  |                         |
   |                                    |                          |                         |
   |                                    | getParameter             |                         |
   |                                    |                          |                         |
   |                                    | currentOp                |                         |
   |                                    |                          |                         |
   |                                    | killOp                   |                         |
   +------------------------------------+--------------------------+-------------------------+
   | Diagnostic Commands                | availableQueryOptions    | connPoolStats           |
   |                                    |                          |                         |
   |                                    | buildInfo                | cursorInfo              |
   |                                    |                          |                         |
   |                                    | collStats                | dbHash                  |
   |                                    |                          |                         |
   |                                    | dataSize                 | diagLogging             |
   |                                    |                          |                         |
   |                                    | dbStats                  | driverOIDTest           |
   |                                    |                          |                         |
   |                                    | explain                  | getCmdLineOpts          |
   |                                    |                          |                         |
   |                                    | features                 | getLog                  |
   |                                    |                          |                         |
   |                                    | listCommands             | hostInfo                |
   |                                    |                          |                         |
   |                                    | listDatabases            | isSelf                  |
   |                                    |                          |                         |
   |                                    | ping                     | netstat                 |
   |                                    |                          |                         |
   |                                    | serverStatus             | profile                 |
   |                                    |                          |                         |
   |                                    | whatsmyuri               | shardConnPoolStats      |
   |                                    |                          |                         |
   |                                    |                          | top                     |
   |                                    |                          |                         |
   |                                    |                          | validate                |
   +------------------------------------+--------------------------+-------------------------+
   | Internal Commands                  | ``-``                    | handshake               |
   |                                    |                          |                         |
   |                                    |                          | \_recvChunkAbort        |
   |                                    |                          |                         |
   |                                    |                          | \_recvChunkCommit       |
   |                                    |                          |                         |
   |                                    |                          | \_recvChunkStart        |
   |                                    |                          |                         |
   |                                    |                          | \_recvChunkStatus       |
   |                                    |                          |                         |
   |                                    |                          | \_replSetFresh          |
   |                                    |                          |                         |
   |                                    |                          | mapreduce.shardedfinish |
   |                                    |                          |                         |
   |                                    |                          | \_transferMods          |
   |                                    |                          |                         |
   |                                    |                          | replSetHeartbeat        |
   |                                    |                          |                         |
   |                                    |                          | replSetGetRBID          |
   |                                    |                          |                         |
   |                                    |                          | \_migrateClone          |
   |                                    |                          |                         |
   |                                    |                          | replSetElect            |
   |                                    |                          |                         |
   |                                    |                          | writeBacksQueued        |
   |                                    |                          |                         |
   |                                    |                          | writebacklisten         |
   +------------------------------------+--------------------------+-------------------------+
   | System Events Auditing Commands    | ``-``                    | logApplicationMessage   |
   +------------------------------------+--------------------------+-------------------------+
