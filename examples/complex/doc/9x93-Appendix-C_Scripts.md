# Appendix C: Scripts
<!-- markdownlint-disable MD013 -->

The scripts listed below are used to query the Oracle data dictionary regrading
TDE information.

## Wallet Information *V\$ENCRYPTION_WALLET*

Information about the encryption wallet.

```SQL
PROMPT V$ENCRYPTION_WALLET

set linesize window
COL WRL_TYPE FOR A10
COL STATUS FOR A20
COL WRL_PARAMETER FOR A33
COL WALLET_TYPE FOR A15
COL PDB_NAME FOR A15

SELECT 
  b.name AS pdb_name, 
  wrl_type, 
  keystore_mode, 
  open_mode,
  wrl_parameter, 
  wallet_type,
  status 
FROM 
  v$encryption_wallet a, 
  v$containers b
WHERE 
  a.con_id=b.con_id;
```

## TDE Key Information *V\$ENCRYPTION_KEYS*

Information about the encryption keys.

```SQL
PROMPT V$ENCRYPTION_KEYS
set linesize window
COL KEY_ID FOR A52
COL ACTIVATION_TIME FOR A17
COL NAME FOR A15
COL TAG FOR A30
SELECT 
  b.name,
  a.key_id,
  trunc (a.activation_time) AS activation_time,
  tag
FROM 
  v$encryption_keys a,
  v$containers b
WHERE
  a.con_id=b.con_id;
```

Information about the encryption keys.

```SQL
set linesize window
COL creator FOR A5
COL key_use FOR A10
COL keystore_type FOR A25
COL origin FOR A10
COL creator_pdbname FOR A15
COL activating_pdbname FOR A15
COL KEY_ID... FOR A10
SELECT
  b.name,
  substr(key_id,1,6)||'...' "KEY_ID...",
  creator,
  key_use,
  keystore_type,
  origin,
  creator_pdbname,
  activating_pdbname 
from 
  v$encryption_keys a ,v$containers b
WHERE
  a.con_id=b.con_id;
```

Information about the encryption keys.

```SQL
set lines window
COL name FOR A10
COL key_id FOR A60
COL creation_time FOR A40
SELECT 
  p.name,
  p.open_mode,
  ek.key_id,
  ek.creation_time,
  ek.key_use
FROM
  v$pdbs p LEFT OUTER JOIN v$encryption_keys ek ON (ek.con_id = p.con_id) 
ORDER BY 
  p.con_id;
```

Information about the encryption keys.

```SQL
PROMPT V$DATABASE_KEY_INFO
SET linesize window
COL NAME FOR A10
COL KEY_ID FOR A50
COL active FOR A10
SELECT
  b.name, 
  encryptionalg,
  masterkeyid,
  masterkey_activated AS active 
FROM
  v$database_key_info a ,v$containers b 
WHERE 
  a.con_id=b.con_id;
```

## Tablespace Information *V\$ENCRYPTED_TABLESPACES*

```SQL
PROMPT v$encrypted_tablespaces
SET linesize window
COL pdb_name FOR A10
COL tbs_name FOR A15
SELECT 
  c.name pdb_name,
  b.name tbs_name,
  a.encryptionalg,
  a.encryptedkey,
  a.masterkeyid,
  a.status
FROM 
  v$encrypted_tablespaces a,
  v$tablespace b,
  v$containers c
WHERE
  b.ts#=a.ts# AND 
  a.con_id=c.con_id AND 
  b.con_id=c.con_id;
```

```SQL
COL owner FOR A15
COL segment_name FOR A20
SELECT
  name, 
  owner,
  segment_name,
  tablespace_name 
FROM
  cdb_segments a,
  v$containers b
WHERE 
  a.con_id=b.con_id AND 
  a.tablespace_name IN (
    SELECT
      d.name
    FROM
      v$encrypted_tablespaces c,
      v$tablespace d
    WHERE
      c.ts#=d.ts#);
```

## Container Information *CDB_ENCRYPTED_COLUMNS*

```SQL
PROMPT cdb_encrypted_columns
COL table_name FOR A15
COL column_name FOR A10
COL owner FOR A15
COL encryption_alg FOR A20

SELECT 
  con_id,
  owner,
  table_name, 
  column_name,
  encryption_alg
FROM 
  cdb_encrypted_columns;
```

## Container Information *V\$CONTAINERS*

```SQL
PROMPT pdb_plug_in_violations
SET linesize window
COL message FOR A50
COL action FOR A50
SET line 200
SELECT 
  b.name,
  type,
  message, 
  action
FROM
  pdb_plug_in_violations a ,
  v$containers b
WHERE 
  a.con_id=b.con_id AND 
  status != 'resolved';
```

## Client Secret Information *V\$CLIENT_SECRETS*

```SQL
PROMPT v$client_secrets
COL owner_dbname FOR A20
COL owner_pdbname FOR A15
COL owner_instance_name FOR A15
COL activation_time FOR A35

SELECT
  owner,
  keystore_type,
  owner_dbname,
  owner_pdbname,
  owner_instance_name,
  creation_time,
  activation_time
FROM
  v$client_secrets;
```
