---
title: 安全性識別碼全域函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlsecurity/ATL::Sids::AccountOps
- atlsecurity/ATL::Sids::Admins
- atlsecurity/ATL::Sids::AnonymousLogon
- atlsecurity/ATL::Sids::AuthenticatedUser
- atlsecurity/ATL::Sids::BackupOps
- atlsecurity/ATL::Sids::Batch
- atlsecurity/ATL::Sids::CreatorGroup
- atlsecurity/ATL::Sids::CreatorGroupServer
- atlsecurity/ATL::Sids::CreatorOwner
- atlsecurity/ATL::Sids::CreatorOwnerServer
- atlsecurity/ATL::Sids::Dialup
- atlsecurity/ATL::Sids::Guests
- atlsecurity/ATL::Sids::Interactive
- atlsecurity/ATL::Sids::Local
- atlsecurity/ATL::Sids::Network
- atlsecurity/ATL::Sids::NetworkService
- atlsecurity/ATL::Sids::Null
- atlsecurity/ATL::Sids::PowerUsers
- atlsecurity/ATL::Sids::PrintOps
- atlsecurity/ATL::Sids::Proxy
- atlsecurity/ATL::Sids::RasServers
- atlsecurity/ATL::Sids::Replicator
- atlsecurity/ATL::Sids::RestrictedCode
- atlsecurity/ATL::Sids::Self
- atlsecurity/ATL::Sids::ServerLogon
- atlsecurity/ATL::Sids::Service
- atlsecurity/ATL::Sids::System
- atlsecurity/ATL::Sids::SystemOps
- atlsecurity/ATL::Sids::TerminalServer
- atlsecurity/ATL::Sids::Users
- atlsecurity/ATL::Sids::World
dev_langs:
- C++
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bcafdeecdc0091039e9bb4008aab4e85f6a34aa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064963"
---
# <a name="security-identifier-global-functions"></a>安全性識別碼全域函式

這些函式會傳回一般的已知 SID 的物件。

> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[Sids::AccountOps](#accountops)|傳回 DOMAIN_ALIAS_RID_ACCOUNT_OPS SID。|
|[Sids::Admins](#admins)|傳回 DOMAIN_ALIAS_RID_ADMINS SID。|
|[Sids::AnonymousLogon](#anonymouslogon)|傳回 SECURITY_ANONYMOUS_LOGON_RID SID。|
|[Sids::AuthenticatedUser](#authenticateduser)|傳回 SECURITY_AUTHENTICATED_USER_RID SID。|
|[Sids::BackupOps](#backupops)|傳回 DOMAIN_ALIAS_RID_BACKUP_OPS SID。|
|[Sids::Batch](#batch)|傳回 SECURITY_BATCH_RID SID。|
|[Sids::CreatorGroup](#creatorgroup)|傳回 SECURITY_CREATOR_GROUP_RID SID。|
|[Sids::CreatorGroupServer](#creatorgroupserver)|傳回 SECURITY_CREATOR_GROUP_SERVER_RID SID。|
|[Sids::CreatorOwner](#creatorowner)|傳回 SECURITY_CREATOR_OWNER_RID SID。|
|[Sids::CreatorOwnerServer](#creatorownerserver)|傳回 SECURITY_CREATOR_OWNER_SERVER_RID SID。|
|[Sids::Dialup](#dialup)|傳回 SECURITY_DIALUP_RID SID。|
|[Sids::Guests](#guests)|傳回 DOMAIN_ALIAS_RID_GUESTS SID。|
|[Sids::Interactive](#interactive)|傳回 SECURITY_INTERACTIVE_RID SID。|
|[Sids::Local](#local)|傳回 SECURITY_LOCAL_RID SID。|
|[Sids::Network](#network)|傳回 SECURITY_NETWORK_RID SID。|
|[Sids::NetworkService](#networkservice)|傳回 SECURITY_NETWORK_SERVICE_RID SID。|
|[Sids::Null](#null)|傳回 SECURITY_NULL_RID SID。|
|[Sids::PreW2KAccess](#prew2kaccess)|傳回 DOMAIN_ALIAS_RID_PREW2KCOMPACCESS SID。|
|[Sids::PowerUsers](#powerusers)|傳回 DOMAIN_ALIAS_RID_POWER_USERS SID。|
|[Sids::PrintOps](#printops)|傳回 DOMAIN_ALIAS_RID_PRINT_OPS SID。|
|[Sids::Proxy](#proxy)|傳回 SECURITY_PROXY_RID SID。|
|[Sids::RasServers](#rasservers)|傳回 DOMAIN_ALIAS_RID_RAS_SERVERS SID。|
|[Sids::Replicator](#replicator)|傳回 DOMAIN_ALIAS_RID_REPLICATOR SID。|
|[Sids::RestrictedCode](#restrictedcode)|傳回 SECURITY_RESTRICTED_CODE_RID SID。|
|[Sids::Self](#self)|傳回 SECURITY_PRINCIPAL_SELF_RID SID。|
|[Sids::ServerLogon](#serverlogon)|傳回 SECURITY_SERVER_LOGON_RID SID。|
|[Sids::Service](#service)|傳回 SECURITY_SERVICE_RID SID。|
|[Sids::System](#system)|傳回 SECURITY_LOCAL_SYSTEM_RID SID。|
|[Sids::SystemOps](#systemops)|傳回 DOMAIN_ALIAS_RID_SYSTEM_OPS SID。|
|[Sids::TerminalServer](#terminalserver)|傳回 SECURITY_TERMINAL_SERVER_RID SID。|
|[Sids::Users](#users)|傳回 DOMAIN_ALIAS_RID_USERS SID。|
|[Sids::World](#world)|傳回 SECURITY_WORLD_RID SID。|

### <a name="requirements"></a>需求

**標頭：** atlsecurity.h

##  <a name="accountops"></a>  Sids::AccountOps

傳回 DOMAIN_ALIAS_RID_ACCOUNT_OPS SID。

```
CSid AccountOps() throw(...);
```

##  <a name="admins"></a>  Sids::Admins

傳回 DOMAIN_ALIAS_RID_ADMINS SID。

```
CSid Admins() throw(...);
```

##  <a name="anonymouslogon"></a>  Sids::AnonymousLogon

傳回 SECURITY_ANONYMOUS_LOGON_RID SID。

```
CSid AnonymousLogon() throw(...);
```

##  <a name="authenticateduser"></a>  Sids::AuthenticatedUser

傳回 SECURITY_AUTHENTICATED_USER_RID SID。

```
CSid AuthenticatedUser() throw(...);
```

##  <a name="backupops"></a>  Sids::BackupOps

傳回 DOMAIN_ALIAS_RID_BACKUP_OPS SID。

```
CSid BackupOps() throw(...);
```

##  <a name="batch"></a>  Sids::Batch

傳回 SECURITY_BATCH_RID SID。

```
CSid Batch() throw(...);
```

##  <a name="creatorgroup"></a>  Sids::CreatorGroup

傳回 SECURITY_CREATOR_GROUP_RID SID。

```
CSid CreatorGroup() throw(...);
```

##  <a name="creatorgroupserver"></a>  Sids::CreatorGroupServer

傳回 SECURITY_CREATOR_GROUP_SERVER_RID SID。

```
CSid CreatorGroupServer() throw(...);
```

##  <a name="creatorowner"></a>  Sids::CreatorOwner

傳回 SECURITY_CREATOR_OWNER_RID SID。

```
CSid CreatorOwner() throw(...);
```

##  <a name="creatorownerserver"></a>  Sids::CreatorOwnerServer

傳回 SECURITY_CREATOR_OWNER_SERVER_RID SID。

```
CSid CreatorOwnerServer() throw(...);
```

##  <a name="dialup"></a>  Sids::Dialup

傳回 SECURITY_DIALUP_RID SID。

```
CSid Dialup() throw(...);
```

##  <a name="guests"></a>  Sids::Guests

傳回 DOMAIN_ALIAS_RID_GUESTS SID。

```
CSid Guests() throw(...);
```

##  <a name="interactive"></a>  Sids::Interactive

傳回 SECURITY_INTERACTIVE_RID SID。

```
CSid Interactive() throw(...);
```

##  <a name="local"></a>  Sids::Local

傳回 SECURITY_LOCAL_RID SID。

```
CSid Local() throw(...);
```

##  <a name="network"></a>  Sids::Network

傳回 SECURITY_NETWORK_RID SID。

```
CSid Network() throw(...);
```

##  <a name="networkservice"></a>  Sids::NetworkService

傳回 SECURITY_NETWORK_SERVICE_RID SID。

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>備註

您可以使用 NetworkService 啟用 NT AUTHORITY\NetworkService 使用者讀取 CPerfMon 安全性物件。 NetworkService 新增 SecurityAttribute ATLServer 程式碼才可登入，在只有 Windows XP Home Edition、 Windows XP Professional、 Windows Server 2003 和更新版本作業系統的 NetworkService 帳戶下的 DLL。

自訂記錄檔的計數器會建立與 Perfmon MMC 中的 ATLServer CPerfMon 類別，檢視記錄檔，雖然會正確出現在 [即時] 檢視時，可能不會出現的計數器。 CPerfMon 自訂效能計數器沒有 「 效能記錄及警示 」 服務 (smlogsvc.exe) 上執行 Windows XP Home Edition、 Windows XP Professional、 Windows Server 2003 （或更新版本） 作業系統的必要權限。 此服務帳戶之下執行"NT AUTHORITY\NetworkService"。

##  <a name="null"></a>  Sids::Null

傳回 SECURITY_NULL_RID SID。

```
CSid Null() throw(...);
```

##  <a name="prew2kaccess"></a>  Sids::PreW2KAccess

傳回 DOMAIN_ALIAS_RID_PREW2KCOMPACCESS SID。

```
CSid PreW2KAccess() throw(...);
```

##  <a name="powerusers"></a>  Sids::PowerUsers

傳回 DOMAIN_ALIAS_RID_POWER_USERS SID。

```
CSid PowerUsers() throw(...);
```

##  <a name="printops"></a>  Sids::PrintOps

傳回 DOMAIN_ALIAS_RID_PRINT_OPS SID。

```
CSid PrintOps() throw(...);
```

##  <a name="proxy"></a>  Sids::Proxy

傳回 SECURITY_PROXY_RID SID。

```
CSid Proxy() throw(...);
```

##  <a name="rasservers"></a>  Sids::RasServers

傳回 DOMAIN_ALIAS_RID_RAS_SERVERS SID。

```
CSid RasServers() throw(...);
```

##  <a name="replicator"></a>  Sids::Replicator

傳回 DOMAIN_ALIAS_RID_REPLICATOR SID。

```
CSid Replicator() throw(...);
```

##  <a name="restrictedcode"></a>  Sids::RestrictedCode

傳回 SECURITY_RESTRICTED_CODE_RID SID。

```
CSid RestrictedCode() throw(...);
```

##  <a name="self"></a>  Sids::Self

傳回 SECURITY_PRINCIPAL_SELF_RID SID。

```
CSid Self() throw(...);
```

##  <a name="serverlogon"></a>  Sids::ServerLogon

傳回 SECURITY_SERVER_LOGON_RID SID。

```
CSid ServerLogon() throw(...);
```

##  <a name="service"></a>  Sids::Service

傳回 SECURITY_SERVICE_RID SID。

```
CSid Service() throw(...);
```

##  <a name="system"></a>  Sids::System

傳回 SECURITY_LOCAL_SYSTEM_RID SID。

```
CSid System() throw(...);
```

##  <a name="systemops"></a>  Sids::SystemOps

傳回 DOMAIN_ALIAS_RID_SYSTEM_OPS SID。

```
CSid SystemOps() throw(...);
```

##  <a name="terminalserver"></a>  Sids::TerminalServer

傳回 SECURITY_TERMINAL_SERVER_RID SID。

```
CSid TerminalServer() throw(...);
```

##  <a name="users"></a>  Sids::Users

傳回 DOMAIN_ALIAS_RID_USERS SID。

```
CSid Users() throw(...);
```

##  <a name="world"></a>  Sids::World

傳回 SECURITY_WORLD_RID SID。

```
CSid World() throw(...);
```

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
