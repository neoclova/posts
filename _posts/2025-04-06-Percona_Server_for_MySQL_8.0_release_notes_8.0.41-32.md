---
title: "[Release Note] Percona Server for MySQL 8.0.41-32"
date: 2025-04-08 14:35:00 +0900
categories: [2. DBMS Release Note, Percona Server for MySQL 8.0]
tags: [DBMS, MySQL, Percona, Release Notes, NeoClova, neoclova, 네오클로바]
image:
  path: /assets/img/posts_2025/Percona_Server_for_MySQL.jpg
  lqip: data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAgGBgcGBQgHBwcJCQgKDBQNDAsLDBkSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hyc5PTgyPC4zNDL/2wBDAQkJCQwLDBgNDRgyIRwhMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjL/wAARCAAQABADASIAAhEBAxEB/8QAGgAAAgMBAQAAAAAAAAAAAAAABAUCAwYBB//EADsQAAIBAgQDBgMFBwUBAAAAAAABAgMRBAUSITEGQVFhEyJxgZEjMoGRobHR8EJicuHwFSMzQ2LC8WKi/8QAGQEAAwEBAQAAAAAAAAAAAAAAAAECAwQF/8QAJhEAAgIBBAICAgMAAAAAAAAAAAECEQMSITEEE0FRYQUTIjNhsf/aAAwDAQACEAMQAAAB8rNZa8T4PUK0KuocUt7ctZosYkxhIUExixpyNnNuSPArxOdEk1Ak+F4sh1F3rlYrXvFJKR0NfMVltMTIyIlaAaKVgAc8LQx22NPIgZT4pI7uWYZAGJWDkW2vEVTo6Ejr6qW8X1vK4zrREdm6WiOjIAqvP3qsyeFWTNdW8+M34ffco50aBprV42JWAdUly5EMuvNUK2N8lKqIlA6R5nh1lFxEViNDKFkxyEEiYAKZPYHg2Er4h2MJFRHiQGp9oNBSR3F0myuwOYvN2F4vdoOc+hglSiQoY+9Pdi7HcKl5ztF8JJd+ykeZHP3YkSak8A20swq1XZfI15chYoCKuI7AUQWGeD6kV+DaI9LLr9mnxcffJKu5SGHozm2uKoQSB4Khf8AeTPhMNnq6WjlgZqksUbSTkfTo5pUsBFg0G2QHq9YqjvFo2mssE4atGvTD7R7WwVkKtEZMQzLIwRkQPEe+Db4UpPheOPTL8Y6XsoOJTDtyzD40FtD0BSYyBT3YkfOBu9OJNSvmEFAH2yH9UPQU5j2XGmdHwTDNXdMSIPqW1DKQqQN2Pi9+l9AoKQAH/2Q==
  alt: Release Note Percona Server for MySQL 8.0.41-32
---

> <a href="https://docs.percona.com/percona-server/8.0/release-notes/8.0.41-32.html" target="_blank">Percona Server for MySQL 8.0.41-32</a> (2025-02-26)
{: .prompt-info }

## Release highlights
### Percona Server for MySQL 8.0.41-32

- Extends the <a href="https://docs.percona.com/percona-server/8.0/encryption-functions.html" target="_blank">Encryption user-defined functions</a> with the following:
> `Encryption UDF 에 다음 기능이 확장되었습니다:`

  - Added support for pkcs1, oaep, or no padding for RSA encrypt and decrypt operations
  > `RSA 암호화 및 복호화 작업에 대해 pkcs1, oaep, 또는 패딩 없음(no padding)을 지원하도록 추가했습니다.`

  - Added support for pkcs1 or pkcs1_pss padding for RSA sign and verify operations
  > `RSA 서명 및 검증 작업에 대해 pkcs1 또는 pkcs1_pss 패딩을 지원하도록 추가했습니다.`

  - Added the encryption_udf.legacy_padding_scheme system variable to manage legacy padding schemes
  > `레거시 패딩 방식을 관리하기 위한 시스템 변수 encryption_udf.legacy_padding_scheme 를 추가했습니다.`

  - Added the character set awareness
  > `character set awareness 기능을 추가했습니다.`

- Improves the <a href="https://docs.percona.com/percona-server/8.0/data-masking-overview.html" target="_blank">Data masking</a> performance by introducing an internal term cache. The new cache speeds up lookups for gen_blocklist() and gen_dictionary() functions by storing dictionary data in memory.
> `내부 용어 캐시를 도입하여 데이터 마스킹 성능을 향상시켰습니다. 이 새로운 캐시는 gen_blocklist() 및 gen_dictionary() 함수의 조회 속도를 높이기 위해 dictionary 데이터를 메모리에 저장합니다.`

Find more detailed information in the <a href="https://docs.percona.com/percona-server/8.0/data-masking-overview.html" target="_blank">Data masking overview</a> and in the <a href="https://docs.percona.com/percona-server/8.0/data-masking-function-list.html" target="_blank">Data masking component functions</a>.

### MySQL 8.0.41
Improvements and bug fixes provided by Oracle for MySQL 8.0.41 and included in Percona Server for MySQL are the following:

- Fixed an assertion in debug builds where certain IO buffer serializations caused system hangs. (Bug #37139618)
> `특정 IO buffer serializations 로 시스템이 멈추는 debug builds 의 assert 오류를 수정했습니다. (Bug #37139618)`

- Resolved a failure when dropping the primary key and adding a new AUTO_INCREMENT column as the primary key in descending order using the INPLACE algorithm resulted in failure. (Bug #36658450)
> `INPLACE 알고리즘을 사용하여 PK 를 삭제하고 새로운 AUTO_INCREMENT 컬럼을 내림차순 PK 로 추가할 때 실패하던 문제를 해결했습니다. (Bug #36658450)`

- Fixed incorrect results, including missing rows, in queries that used a descending primary key with the index_merge optimization. (Bug #106207, Bug #33767814)
> `index_merge 최적화를 사용하고 내림차순 PK 를 가진 쿼리에서 누락된 row 등 잘못된 결과가 발생하던 문제를 수정했습니다. (Bug #106207, Bug #33767814)`

- Addressed a replication channel issue where MySQL failed to stop the channel properly when large transactions were being processed, and STOP REPLICA was requested. This issue also prevented graceful server shutdown, requiring process termination or system restart. (Bug #115966, Bug #37008345)
> `대용량 트랜잭션 처리 중 STOP REPLICA 명령이 실행될 때 replication channel 이 정상적으로 중지되지 않는 문제를 해결했습니다. 이 문제는 서버의 정상적인 종료를 방해하며, 프로세스 강제로 종료하거나 시스템 재시작이 필요했습니다. (Bug #115966, Bug #37008345)`

Find the complete list of bug fixes and changes in the MySQL 8.0.41 Release Notes.

## Improvements
- <a href="https://perconadev.atlassian.net/browse/PS-8389" target="_blank">PS-8389</a> : Extends the Encryption user-defined functions to incorporate the new and modified asymmetric key functionality introduced by Oracle in MySQL 8.0.30 Enterprise Encryption Component Function Descriptions.
> `암호화 사용자 정의 함수를 확장하여, Oracle 이 MySQL 8.0.30 Enterprise 암호화 컴포넌트에서 도입한 새로운 비대칭 키 기능 및 수정된 기능을 통합합니다.`

- <a href="https://perconadev.atlassian.net/browse/PS-9148" target="_blank">PS-9148</a> : Extends the Data masking with new additions from MySQL 8.3.0 Enterprise Data Masking and De-Identification Component Variables.
> `데이터 마스킹 기능을 확장하여 MySQL 8.3.0 Enterprise 데이터 마스킹 및 비식별화 컴포넌트 변수에서 추가된 새로운 기능을 통합합니다.`

## Bug Fixes
- <a href="https://perconadev.atlassian.net/browse/PS-9391" target="_blank">PS-9391</a> : The replication broke with the error HA_ERR_KEY_NOT_FOUND when the slave_rows_search_algorithms were set to INDEX_SCAN,HASH_SCAN.
> `slave_rows_search_algorithms 값을 INDEX_SCAN, HASH_SCAN 으로 설정했을 때 복제가 HA_ERR_KEY_NOT_FOUND 오류와 함께 중단되었습니다.`

- <a href="https://perconadev.atlassian.net/browse/PS-9416" target="_blank">PS-9416</a> : The error messages from the Key Management Interoperability Protocol (KMIP) component were not descriptive.
> `키 관리 상호 운용성 프로토콜(KMIP) 컴포넌트의 오류 메시지가 충분히 설명적이지 않았습니다.`

- <a href="https://perconadev.atlassian.net/browse/PS-9537" target="_blank">PS-9537</a> : When building a new component that used mysql_command_xxx services (such as mysql_command_factory, mysql_command_query, etc.), it was impossible to reuse the same connection to run multiple queries. This issue was observed with SELECT queries, but it may also apply to INSERT, UPDATE, and DELETE operations.
> `mysql_command_xxx 서비스(mysql_command_factory, mysql_command_query 등)를 사용하는 새로운 컴포넌트를 빌드할 때, 동일한 연결을 재사용하여 여러 개의 쿼리를 실행하는 것이 불가능했습니다. 이 문제는 SELECT 쿼리에서 확인되었지만, INSERT, UPDATE, DELETE 작업에도 영향을 미칠 가능성이 있습니다.`

- <a href="https://perconadev.atlassian.net/browse/PS-9542" target="_blank">PS-9542</a> : Added Clang-19 to Azure pipelines, and fixed the clang-19 compilation issues.
> `Azure 파이프라인에 Clang-19 를 추가하고, Clang-19 컴파일 문제를 해결했습니다.`

- <a href="https://perconadev.atlassian.net/browse/PS-9551" target="_blank">PS-9551</a> : When building components that utilized MySQL command services (for example, mysq _command_factory, mysql_command_query), reusing a single connection for multiple queries was previously impossible. This limitation was observed with SELECT queries but may have also impacted INSERT, UPDATE, and DELETE operations.
> `MySQL 명령 서비스(mysql_command_factory, mysql_command_query 등)를 사용하는 컴포넌트를 빌드할 때, 단일 연결을 재사용하여 여러 개의 쿼리를 실행하는 것이 이전에는 불가능했습니다. 이 제한 사항은 SELECT 쿼리에서 확인되었지만, INSERT, UPDATE, DELETE 작업에도 영향을 미쳤을 가능성이 있습니다.`

- <a href="https://perconadev.atlassian.net/browse/PS-9611" target="_blank">PS-9611</a> : An assertion failure occurred during server shutdown: !is_set() || m_can_overwrite_status.
> `서버 종료 중에 어설션 오류가 발생했습니다: !is_set() || m_can_overwrite_status.`

- <a href="https://perconadev.atlassian.net/browse/PS-9612" target="_blank">PS-9612</a> : Percona Server build failed if more than 128 threads were available. Percona merged the fix from MariaDB.
> `Percona Server 빌드 시 128개 이상의 스레드가 사용 가능한 경우 실패하는 문제가 발생했습니다. Percona 는 이 문제를 해결하기 위해 MariaDB 의 패치를 병합했습니다.`

- <a href="https://perconadev.atlassian.net/browse/PS-9509" target="_blank">PS-9509</a> : Percona Server did not track the global_connection_memory when setting the thread_handling='pool-of-threads' option.
> `Percona Server 에서 thread_handling='pool-of-threads' 옵션을 설정할 때 global_connection_memory 를 추적하지 않았습니다.`
- <a href="https://perconadev.atlassian.net/browse/PS-9614" target="_blank">PS-9614</a> : When the pool-of-threads was enabled, the timer_thread was missing if mysqld had been started with the --daemonize option.
> `pool-of-threads 가 활성화된 상태에서 --daemonize 옵션과 함께 mysqld를 시작하면 timer_thread 누락되는 문제가 발생했습니다`