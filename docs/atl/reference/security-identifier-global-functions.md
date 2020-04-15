---
title: 安全識別子通用函數
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
ms.openlocfilehash: 83326c13de7585806ab841f728f587f1131b5e8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325985"
---
# <a name="security-identifier-global-functions"></a>安全識別子通用函數

這些函數返回常見的已知 SID 物件。

> [!IMPORTANT]
> 下表中列出的函數不能在 Windows 執行時中執行的應用程式中使用。

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
|[希德::世界](#world)|傳回 SECURITY_WORLD_RID SID。|

### <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="sidsaccountops"></a><a name="accountops"></a>Sids::帳戶

傳回 DOMAIN_ALIAS_RID_ACCOUNT_OPS SID。

```
CSid AccountOps() throw(...);
```

## <a name="sidsadmins"></a><a name="admins"></a>Sids::管理員

傳回 DOMAIN_ALIAS_RID_ADMINS SID。

```
CSid Admins() throw(...);
```

## <a name="sidsanonymouslogon"></a><a name="anonymouslogon"></a>Sids::匿名登錄

傳回 SECURITY_ANONYMOUS_LOGON_RID SID。

```
CSid AnonymousLogon() throw(...);
```

## <a name="sidsauthenticateduser"></a><a name="authenticateduser"></a>Sids::經過身份驗證的使用者

傳回 SECURITY_AUTHENTICATED_USER_RID SID。

```
CSid AuthenticatedUser() throw(...);
```

## <a name="sidsbackupops"></a><a name="backupops"></a>Sids::備份操作

傳回 DOMAIN_ALIAS_RID_BACKUP_OPS SID。

```
CSid BackupOps() throw(...);
```

## <a name="sidsbatch"></a><a name="batch"></a>Sids::批次

傳回 SECURITY_BATCH_RID SID。

```
CSid Batch() throw(...);
```

## <a name="sidscreatorgroup"></a><a name="creatorgroup"></a>Sids::創造者組

傳回 SECURITY_CREATOR_GROUP_RID SID。

```
CSid CreatorGroup() throw(...);
```

## <a name="sidscreatorgroupserver"></a><a name="creatorgroupserver"></a>Sids::創造者群伺服器

傳回 SECURITY_CREATOR_GROUP_SERVER_RID SID。

```
CSid CreatorGroupServer() throw(...);
```

## <a name="sidscreatorowner"></a><a name="creatorowner"></a>Sids::創造者擁有者

傳回 SECURITY_CREATOR_OWNER_RID SID。

```
CSid CreatorOwner() throw(...);
```

## <a name="sidscreatorownerserver"></a><a name="creatorownerserver"></a>Sids::創造者擁有者伺服器

傳回 SECURITY_CREATOR_OWNER_SERVER_RID SID。

```
CSid CreatorOwnerServer() throw(...);
```

## <a name="sidsdialup"></a><a name="dialup"></a>希德::D亞里普

傳回 SECURITY_DIALUP_RID SID。

```
CSid Dialup() throw(...);
```

## <a name="sidsguests"></a><a name="guests"></a>希德::客人

傳回 DOMAIN_ALIAS_RID_GUESTS SID。

```
CSid Guests() throw(...);
```

## <a name="sidsinteractive"></a><a name="interactive"></a>Sids::互動

傳回 SECURITY_INTERACTIVE_RID SID。

```
CSid Interactive() throw(...);
```

## <a name="sidslocal"></a><a name="local"></a>Sids::本地端

傳回 SECURITY_LOCAL_RID SID。

```
CSid Local() throw(...);
```

## <a name="sidsnetwork"></a><a name="network"></a>Sids::網路

傳回 SECURITY_NETWORK_RID SID。

```
CSid Network() throw(...);
```

## <a name="sidsnetworkservice"></a><a name="networkservice"></a>Sids::網路服務

傳回 SECURITY_NETWORK_SERVICE_RID SID。

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>備註

使用網路服務使 NT AUTHORITY_網路服務使用者能夠讀取 CPerfMon 安全物件。 網路服務向 ATLServer 代碼添加了一個安全屬性,該代碼將允許 DLL 在 Windows XP 家庭版、Windows XP 專業版、Windows Server 2003 和更大的作業系統上的網路服務帳戶下登錄。

在 Perfmon MMC 中使用 ATLServer CPerfMon 類創建自訂日誌計數器時,在查看日誌檔時可能不會顯示這些計數器,儘管它們將在即時檢視中正確顯示。 CPerfMon 自定義性能計數器在 Windows XP 主版、Windows XP 專業版、Windows Server 2003(或更高版)操作系統上的"性能日誌和警報"服務 (smlogsvc.exe) 下沒有運行所需的許可權。 此服務在「NT AUTHORITY_網路服務」帳戶下運行。

## <a name="sidsnull"></a><a name="null"></a>Sids::空

傳回 SECURITY_NULL_RID SID。

```
CSid Null() throw(...);
```

## <a name="sidsprew2kaccess"></a><a name="prew2kaccess"></a>Sids::PreW2KAccess

傳回 DOMAIN_ALIAS_RID_PREW2KCOMPACCESS SID。

```
CSid PreW2KAccess() throw(...);
```

## <a name="sidspowerusers"></a><a name="powerusers"></a>Sids::P使用者

傳回 DOMAIN_ALIAS_RID_POWER_USERS SID。

```
CSid PowerUsers() throw(...);
```

## <a name="sidsprintops"></a><a name="printops"></a>希德::P林圖普斯

傳回 DOMAIN_ALIAS_RID_PRINT_OPS SID。

```
CSid PrintOps() throw(...);
```

## <a name="sidsproxy"></a><a name="proxy"></a>希德::P羅西

傳回 SECURITY_PROXY_RID SID。

```
CSid Proxy() throw(...);
```

## <a name="sidsrasservers"></a><a name="rasservers"></a>Sids::拉塞塞

傳回 DOMAIN_ALIAS_RID_RAS_SERVERS SID。

```
CSid RasServers() throw(...);
```

## <a name="sidsreplicator"></a><a name="replicator"></a>Sids::複製器

傳回 DOMAIN_ALIAS_RID_REPLICATOR SID。

```
CSid Replicator() throw(...);
```

## <a name="sidsrestrictedcode"></a><a name="restrictedcode"></a>Sids::受限代碼

傳回 SECURITY_RESTRICTED_CODE_RID SID。

```
CSid RestrictedCode() throw(...);
```

## <a name="sidsself"></a><a name="self"></a>希德::自我

傳回 SECURITY_PRINCIPAL_SELF_RID SID。

```
CSid Self() throw(...);
```

## <a name="sidsserverlogon"></a><a name="serverlogon"></a>Sids::伺服器日誌

傳回 SECURITY_SERVER_LOGON_RID SID。

```
CSid ServerLogon() throw(...);
```

## <a name="sidsservice"></a><a name="service"></a>希德::服務

傳回 SECURITY_SERVICE_RID SID。

```
CSid Service() throw(...);
```

## <a name="sidssystem"></a><a name="system"></a>Sids::系統

傳回 SECURITY_LOCAL_SYSTEM_RID SID。

```
CSid System() throw(...);
```

## <a name="sidssystemops"></a><a name="systemops"></a>Sids::系統操作

傳回 DOMAIN_ALIAS_RID_SYSTEM_OPS SID。

```
CSid SystemOps() throw(...);
```

## <a name="sidsterminalserver"></a><a name="terminalserver"></a>Sids::終端伺服器

傳回 SECURITY_TERMINAL_SERVER_RID SID。

```
CSid TerminalServer() throw(...);
```

## <a name="sidsusers"></a><a name="users"></a>Sids:使用者

傳回 DOMAIN_ALIAS_RID_USERS SID。

```
CSid Users() throw(...);
```

## <a name="sidsworld"></a><a name="world"></a>希德::世界

傳回 SECURITY_WORLD_RID SID。

```
CSid World() throw(...);
```

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
