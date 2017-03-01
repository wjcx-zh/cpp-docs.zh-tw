---
title: "安全性識別碼的全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 9e51fe30b0519514df34f1a77b1e731f51047520
ms.lasthandoff: 02/24/2017

---
# <a name="security-identifier-global-functions"></a>安全性識別碼的全域函式
這些函式傳回物件的一般已知的 SID。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
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
 **標頭︰** atlsecurity.h 

##  <a name="a-nameaccountopsa--sidsaccountops"></a><a name="accountops"></a>Sids::AccountOps  
 傳回 DOMAIN_ALIAS_RID_ACCOUNT_OPS SID。    
  
```
CSid AccountOps() throw(...);
```  
  
##  <a name="a-nameadminsa--sidsadmins"></a><a name="admins"></a>Sids::Admins  
 傳回 DOMAIN_ALIAS_RID_ADMINS SID。  
```
CSid Admins() throw(...);
```  
  
##  <a name="a-nameanonymouslogona--sidsanonymouslogon"></a><a name="anonymouslogon"></a>Sids::AnonymousLogon  
 傳回 SECURITY_ANONYMOUS_LOGON_RID SID。  
```
CSid AnonymousLogon() throw(...);
```  
  
##  <a name="a-nameauthenticatedusera--sidsauthenticateduser"></a><a name="authenticateduser"></a>Sids::AuthenticatedUser  
 傳回 SECURITY_AUTHENTICATED_USER_RID SID。  
```
CSid AuthenticatedUser() throw(...);
```  
  
##  <a name="a-namebackupopsa--sidsbackupops"></a><a name="backupops"></a>Sids::BackupOps  
 傳回 DOMAIN_ALIAS_RID_BACKUP_OPS SID。  
```
CSid BackupOps() throw(...);
```  
  
##  <a name="a-namebatcha--sidsbatch"></a><a name="batch"></a>Sids::Batch  
 傳回 SECURITY_BATCH_RID SID。  
```
CSid Batch() throw(...);
```  
  
##  <a name="a-namecreatorgroupa--sidscreatorgroup"></a><a name="creatorgroup"></a>Sids::CreatorGroup  
 傳回 SECURITY_CREATOR_GROUP_RID SID。  
```
CSid CreatorGroup() throw(...);
```  
  
##  <a name="a-namecreatorgroupservera--sidscreatorgroupserver"></a><a name="creatorgroupserver"></a>Sids::CreatorGroupServer  
 傳回 SECURITY_CREATOR_GROUP_SERVER_RID SID。  
```
CSid CreatorGroupServer() throw(...);
```  
  
##  <a name="a-namecreatorownera--sidscreatorowner"></a><a name="creatorowner"></a>Sids::CreatorOwner  
 傳回 SECURITY_CREATOR_OWNER_RID SID。  
```
CSid CreatorOwner() throw(...);
```  
  
##  <a name="a-namecreatorownerservera--sidscreatorownerserver"></a><a name="creatorownerserver"></a>Sids::CreatorOwnerServer  
 傳回 SECURITY_CREATOR_OWNER_SERVER_RID SID。  
```
CSid CreatorOwnerServer() throw(...);
```  
  
##  <a name="a-namedialupa--sidsdialup"></a><a name="dialup"></a>Sids::Dialup  
 傳回 SECURITY_DIALUP_RID SID。  
```
CSid Dialup() throw(...);
```  
  
##  <a name="a-nameguestsa--sidsguests"></a><a name="guests"></a>Sids::Guests  
 傳回 DOMAIN_ALIAS_RID_GUESTS SID。  
```
CSid Guests() throw(...);
```  
  
##  <a name="a-nameinteractivea--sidsinteractive"></a><a name="interactive"></a>Sids::Interactive  
 傳回 SECURITY_INTERACTIVE_RID SID。  
```
CSid Interactive() throw(...);
```  
  
##  <a name="a-namelocala--sidslocal"></a><a name="local"></a>Sids::Local  
 傳回 SECURITY_LOCAL_RID SID。  
```
CSid Local() throw(...);
```  
  
##  <a name="a-namenetworka--sidsnetwork"></a><a name="network"></a>Sids::Network  
 傳回 SECURITY_NETWORK_RID SID。  
```
CSid Network() throw(...);
```  
  
##  <a name="a-namenetworkservicea--sidsnetworkservice"></a><a name="networkservice"></a>Sids::NetworkService  
 傳回 SECURITY_NETWORK_SERVICE_RID SID。  
```
CSid NetworkService() throw(...);
```  
  
### <a name="remarks"></a>備註  
 使用網路服務，讓 NT AUTHORITY\NetworkService 使用者讀取 CPerfMon 安全性物件。 NetworkService ATLServer 程式碼以便在網路服務帳戶登入的 DLL 加入 SecurityAttribute[!INCLUDE[WinXpFamily](../../atl/reference/includes/winxpfamily_md.md)]和更高的作業系統。  
  
 自訂記錄計數器建立時與 ATLServer CPerfMon Perfmon MMC 中的類別，不過，它們會正確顯示即時檢視中檢視記錄檔時，可能不會出現計數器。 CPerfMon 自訂效能計數器沒有必要權限來執行 「 效能記錄及警示 」 服務 (smlogsvc.exe) [!INCLUDE[WinXpFamily](../../atl/reference/includes/winxpfamily_md.md)] （或以上） 的作業系統。 此服務帳戶之下執行"NT AUTHORITY\NetworkService"。  
  
##  <a name="a-namenulla--sidsnull"></a><a name="null"></a>Sids::Null  
 傳回 SECURITY_NULL_RID SID。  
```
CSid Null() throw(...);
```  
  
##  <a name="a-nameprew2kaccessa--sidsprew2kaccess"></a><a name="prew2kaccess"></a>Sids::PreW2KAccess  
 傳回 DOMAIN_ALIAS_RID_PREW2KCOMPACCESS SID。  
```
CSid PreW2KAccess() throw(...);
```  
  
##  <a name="a-namepowerusersa--sidspowerusers"></a><a name="powerusers"></a>Sids::PowerUsers  
 傳回 DOMAIN_ALIAS_RID_POWER_USERS SID。  
```
CSid PowerUsers() throw(...);
```  
  
##  <a name="a-nameprintopsa--sidsprintops"></a><a name="printops"></a>Sids::PrintOps  
 傳回 DOMAIN_ALIAS_RID_PRINT_OPS SID。  
```
CSid PrintOps() throw(...);
```  
  
##  <a name="a-nameproxya--sidsproxy"></a><a name="proxy"></a>Sids::Proxy  
 傳回 SECURITY_PROXY_RID SID。  
```
CSid Proxy() throw(...);
```  
  
##  <a name="a-namerasserversa--sidsrasservers"></a><a name="rasservers"></a>Sids::RasServers  
 傳回 DOMAIN_ALIAS_RID_RAS_SERVERS SID。  
```
CSid RasServers() throw(...);
```  
  
##  <a name="a-namereplicatora--sidsreplicator"></a><a name="replicator"></a>Sids::Replicator  
 傳回 DOMAIN_ALIAS_RID_REPLICATOR SID。  
```
CSid Replicator() throw(...);
```  
  
##  <a name="a-namerestrictedcodea--sidsrestrictedcode"></a><a name="restrictedcode"></a>Sids::RestrictedCode  
 傳回 SECURITY_RESTRICTED_CODE_RID SID。  
```
CSid RestrictedCode() throw(...);
```  
  
##  <a name="a-nameselfa--sidsself"></a><a name="self"></a>Sids::Self  
 傳回 SECURITY_PRINCIPAL_SELF_RID SID。  
```
CSid Self() throw(...);
```  
  
##  <a name="a-nameserverlogona--sidsserverlogon"></a><a name="serverlogon"></a>Sids::ServerLogon  
 傳回 SECURITY_SERVER_LOGON_RID SID。  
```
CSid ServerLogon() throw(...);
```  
  
##  <a name="a-nameservicea--sidsservice"></a><a name="service"></a>Sids::Service  
 傳回 SECURITY_SERVICE_RID SID。  
```
CSid Service() throw(...);
```  
  
##  <a name="a-namesystema--sidssystem"></a><a name="system"></a>Sids::System  
 傳回 SECURITY_LOCAL_SYSTEM_RID SID。  
```
CSid System() throw(...);
```  
  
##  <a name="a-namesystemopsa--sidssystemops"></a><a name="systemops"></a>Sids::SystemOps  
 傳回 DOMAIN_ALIAS_RID_SYSTEM_OPS SID。  
```
CSid SystemOps() throw(...);
```  
  
##  <a name="a-nameterminalservera--sidsterminalserver"></a><a name="terminalserver"></a>Sids::TerminalServer  
 傳回 SECURITY_TERMINAL_SERVER_RID SID。  
```
CSid TerminalServer() throw(...);
```  
  
##  <a name="a-nameusersa--sidsusers"></a><a name="users"></a>Sids::Users  
 傳回 DOMAIN_ALIAS_RID_USERS SID。  
```
CSid Users() throw(...);
```  
  
##  <a name="a-nameworlda--sidsworld"></a><a name="world"></a>Sids::World  
 傳回 SECURITY_WORLD_RID SID。  
```
CSid World() throw(...);
```  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)

