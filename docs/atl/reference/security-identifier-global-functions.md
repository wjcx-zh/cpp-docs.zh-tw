---
title: 安全識別碼全域函式
ms.date: 11/04/2016
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
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
ms.openlocfilehash: e040cbb76e851bd323360f4f5ae602f9c73651d1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834475"
---
# <a name="security-identifier-global-functions"></a>安全識別碼全域函式

這些函數會傳回常見的已知 SID 物件。

> [!IMPORTANT]
> 下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|名稱|描述|
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
|[Sid：： World](#world)|傳回 SECURITY_WORLD_RID SID。|

### <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="sidsaccountops"></a><a name="accountops"></a> Sid：： AccountOps

傳回 DOMAIN_ALIAS_RID_ACCOUNT_OPS SID。

```
CSid AccountOps() throw(...);
```

## <a name="sidsadmins"></a><a name="admins"></a> Sid：： Admins

傳回 DOMAIN_ALIAS_RID_ADMINS SID。

```
CSid Admins() throw(...);
```

## <a name="sidsanonymouslogon"></a><a name="anonymouslogon"></a> Sid：： AnonymousLogon

傳回 SECURITY_ANONYMOUS_LOGON_RID SID。

```
CSid AnonymousLogon() throw(...);
```

## <a name="sidsauthenticateduser"></a><a name="authenticateduser"></a> Sid：： AuthenticatedUser

傳回 SECURITY_AUTHENTICATED_USER_RID SID。

```
CSid AuthenticatedUser() throw(...);
```

## <a name="sidsbackupops"></a><a name="backupops"></a> Sid：： BackupOps

傳回 DOMAIN_ALIAS_RID_BACKUP_OPS SID。

```
CSid BackupOps() throw(...);
```

## <a name="sidsbatch"></a><a name="batch"></a> Sid：： Batch

傳回 SECURITY_BATCH_RID SID。

```
CSid Batch() throw(...);
```

## <a name="sidscreatorgroup"></a><a name="creatorgroup"></a> Sid：： CreatorGroup

傳回 SECURITY_CREATOR_GROUP_RID SID。

```
CSid CreatorGroup() throw(...);
```

## <a name="sidscreatorgroupserver"></a><a name="creatorgroupserver"></a> Sid：： CreatorGroupServer

傳回 SECURITY_CREATOR_GROUP_SERVER_RID SID。

```
CSid CreatorGroupServer() throw(...);
```

## <a name="sidscreatorowner"></a><a name="creatorowner"></a> Sid：： CreatorOwner

傳回 SECURITY_CREATOR_OWNER_RID SID。

```
CSid CreatorOwner() throw(...);
```

## <a name="sidscreatorownerserver"></a><a name="creatorownerserver"></a> Sid：： CreatorOwnerServer

傳回 SECURITY_CREATOR_OWNER_SERVER_RID SID。

```
CSid CreatorOwnerServer() throw(...);
```

## <a name="sidsdialup"></a><a name="dialup"></a> Sid：:D ialup

傳回 SECURITY_DIALUP_RID SID。

```
CSid Dialup() throw(...);
```

## <a name="sidsguests"></a><a name="guests"></a> Sid：：來賓

傳回 DOMAIN_ALIAS_RID_GUESTS SID。

```
CSid Guests() throw(...);
```

## <a name="sidsinteractive"></a><a name="interactive"></a> Sid：： Interactive

傳回 SECURITY_INTERACTIVE_RID SID。

```
CSid Interactive() throw(...);
```

## <a name="sidslocal"></a><a name="local"></a> Sid：： Local

傳回 SECURITY_LOCAL_RID SID。

```
CSid Local() throw(...);
```

## <a name="sidsnetwork"></a><a name="network"></a> Sid：： Network

傳回 SECURITY_NETWORK_RID SID。

```
CSid Network() throw(...);
```

## <a name="sidsnetworkservice"></a><a name="networkservice"></a> Sid：： NetworkService

傳回 SECURITY_NETWORK_SERVICE_RID SID。

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>備註

使用 NetworkService 讓 NT AUTHORITY\NetworkService 使用者能夠讀取 CPerfMon 安全性物件。 NetworkService 將 SecurityAttribute 新增至 ATLServer 程式碼，這可讓 DLL 在 Windows XP Home Edition、Windows XP Professional、Windows Server 2003 及更高版本的作業系統上，于 NetworkService 帳戶下登入。

當您在 Perfmon MMC 中使用 ATLServer CPerfMon 類別建立自訂記錄檔計數器時，在查看記錄檔時可能不會顯示計數器，不過它們會在即時視圖中正確顯示。 CPerfMon 自訂效能計數器沒有在 Windows XP Home Edition、Windows XP Professional、Windows Server 2003 (或更高) 作業系統上的 "效能記錄檔及警示" 服務 ( # A0) 下執行的必要許可權。 此服務會在 "NT AUTHORITY\NetworkService" 帳戶下執行。

## <a name="sidsnull"></a><a name="null"></a> Sid：： Null

傳回 SECURITY_NULL_RID SID。

```
CSid Null() throw(...);
```

## <a name="sidsprew2kaccess"></a><a name="prew2kaccess"></a> Sid：:P reW2KAccess

傳回 DOMAIN_ALIAS_RID_PREW2KCOMPACCESS SID。

```
CSid PreW2KAccess() throw(...);
```

## <a name="sidspowerusers"></a><a name="powerusers"></a> Sid：:P owerUsers

傳回 DOMAIN_ALIAS_RID_POWER_USERS SID。

```
CSid PowerUsers() throw(...);
```

## <a name="sidsprintops"></a><a name="printops"></a> Sid：:P rintOps

傳回 DOMAIN_ALIAS_RID_PRINT_OPS SID。

```
CSid PrintOps() throw(...);
```

## <a name="sidsproxy"></a><a name="proxy"></a> Sid：:P roxy

傳回 SECURITY_PROXY_RID SID。

```
CSid Proxy() throw(...);
```

## <a name="sidsrasservers"></a><a name="rasservers"></a> Sid：： RasServers

傳回 DOMAIN_ALIAS_RID_RAS_SERVERS SID。

```
CSid RasServers() throw(...);
```

## <a name="sidsreplicator"></a><a name="replicator"></a> Sid：：複寫器

傳回 DOMAIN_ALIAS_RID_REPLICATOR SID。

```
CSid Replicator() throw(...);
```

## <a name="sidsrestrictedcode"></a><a name="restrictedcode"></a> Sid：： RestrictedCode

傳回 SECURITY_RESTRICTED_CODE_RID SID。

```
CSid RestrictedCode() throw(...);
```

## <a name="sidsself"></a><a name="self"></a> Sid：： Self

傳回 SECURITY_PRINCIPAL_SELF_RID SID。

```
CSid Self() throw(...);
```

## <a name="sidsserverlogon"></a><a name="serverlogon"></a> Sid：： ServerLogon

傳回 SECURITY_SERVER_LOGON_RID SID。

```
CSid ServerLogon() throw(...);
```

## <a name="sidsservice"></a><a name="service"></a> Sid：： Service

傳回 SECURITY_SERVICE_RID SID。

```
CSid Service() throw(...);
```

## <a name="sidssystem"></a><a name="system"></a> Sid：： System

傳回 SECURITY_LOCAL_SYSTEM_RID SID。

```
CSid System() throw(...);
```

## <a name="sidssystemops"></a><a name="systemops"></a> Sid：： SystemOps

傳回 DOMAIN_ALIAS_RID_SYSTEM_OPS SID。

```
CSid SystemOps() throw(...);
```

## <a name="sidsterminalserver"></a><a name="terminalserver"></a> Sid：： TerminalServer

傳回 SECURITY_TERMINAL_SERVER_RID SID。

```
CSid TerminalServer() throw(...);
```

## <a name="sidsusers"></a><a name="users"></a> Sid：： Users

傳回 DOMAIN_ALIAS_RID_USERS SID。

```
CSid Users() throw(...);
```

## <a name="sidsworld"></a><a name="world"></a> Sid：： World

傳回 SECURITY_WORLD_RID SID。

```
CSid World() throw(...);
```

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)
