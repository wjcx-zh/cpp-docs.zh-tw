---
title: "CAccessToken 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATLSECURITY/CAccessToken
- ATL.CAccessToken
- CAccessToken
- ATL::CAccessToken
dev_langs:
- C++
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
caps.latest.revision: 24
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
ms.openlocfilehash: 79845a2be4f79a1ee94a9440e8508bcb0e38bcdd
ms.lasthandoff: 02/24/2017

---
# <a name="caccesstoken-class"></a>CAccessToken 類別
這個類別是存取權杖的包裝函式。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAccessToken
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAccessToken:: ~ CAccessToken](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAccessToken::Attach](#attach)|呼叫這個方法提供的存取權的語彙基元控制代碼的擁有權。|  
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|呼叫這個方法來判斷指定的 SID 是否已啟用在`CAccessToken`物件。|  
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|呼叫這個方法來建立新的模擬存取權杖。|  
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|呼叫這個方法來建立新的主要權杖。|  
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|呼叫這個方法來建立新的處理程序所表示的使用者安全性內容中執行`CAccessToken`物件。|  
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|呼叫這個方法來建立新的限制`CAccessToken`物件。|  
|[CAccessToken::Detach](#detach)|呼叫這個方法，以撤銷存取權杖的擁有權。|  
|[CAccessToken::DisablePrivilege](#disableprivilege)|呼叫這個方法，以停用中的權限`CAccessToken`物件。|  
|[CAccessToken::DisablePrivileges](#disableprivileges)|呼叫這個方法，以停用中的一個或多個權限`CAccessToken`物件。|  
|[CAccessToken::EnablePrivilege](#enableprivilege)|呼叫這個方法來啟用的權限在`CAccessToken`物件。|  
|[CAccessToken::EnablePrivileges](#enableprivileges)|呼叫這個方法來啟用中的一個或多個權限`CAccessToken`物件。|  
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|呼叫此方法以傳回`CAccessToken`物件的預設 DACL。|  
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|呼叫此方法來取得`CAccessToken`物件等於目前的執行緒作用中的存取權杖。|  
|[CAccessToken::GetGroups](#getgroups)|呼叫此方法以傳回`CAccessToken`物件的語彙基元的群組。|  
|[CAccessToken::GetHandle](#gethandle)|呼叫這個方法來擷取存取權杖的處理常式。|  
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|呼叫這個方法來取得存取權杖中的模擬等級。|  
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|呼叫此方法以取得相關聯的登入工作階段識別碼`CAccessToken`物件。|  
|[CAccessToken::GetLogonSid](#getlogonsid)|呼叫此方法以取得相關聯的登入 SID`CAccessToken`物件。|  
|[CAccessToken::GetOwner](#getowner)|呼叫此方法以取得相關聯的擁有者`CAccessToken`物件。|  
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|呼叫此方法以取得相關聯的主要群組`CAccessToken`物件。|  
|[CAccessToken::GetPrivileges](#getprivileges)|呼叫此方法以取得相關聯的權限`CAccessToken`物件。|  
|[CAccessToken::GetProcessToken](#getprocesstoken)|呼叫這個方法，以所指處理序的存取權杖初始化 `CAccessToken`。|  
|[CAccessToken::GetProfile](#getprofile)|呼叫此方法來取得指向 使用者設定檔相關聯的控制代碼`CAccessToken`物件。|  
|[CAccessToken::GetSource](#getsource)|呼叫此方法來取得來源的`CAccessToken`物件。|  
|[CAccessToken::GetStatistics](#getstatistics)|呼叫此方法以取得相關聯的資訊`CAccessToken`物件。|  
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|呼叫此方法以取得相關聯的終端機服務工作階段識別碼`CAccessToken`物件。|  
|[CAccessToken::GetThreadToken](#getthreadtoken)|呼叫此方法以初始化`CAccessToken`給定執行緒的權杖。|  
|[CAccessToken::GetTokenId](#gettokenid)|呼叫此方法以取得相關聯的語彙基元 ID`CAccessToken`物件。|  
|[CAccessToken::GetType](#gettype)|呼叫這個方法來取得的權杖類型`CAccessToken`物件。|  
|[CAccessToken::GetUser](#getuser)|呼叫這個方法來識別相關聯的使用者`CAccessToken`物件。|  
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|呼叫此方法來取得指向 使用者設定檔相關聯的控制代碼`CAccessToken`物件。|  
|[CAccessToken::Impersonate](#impersonate)|呼叫這個方法來指派模擬`CAccessToken`到往來文章。|  
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|呼叫此方法可讓呼叫的執行緒來模擬登入之使用者的安全性內容。|  
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|呼叫這個方法來測試是否`CAccessToken`物件包含一份 Sid 限制。|  
|[CAccessToken::LoadUserProfile](#loaduserprofile)|呼叫這個方法來載入使用者設定檔相關聯`CAccessToken`物件。|  
|[CAccessToken::LogonUser](#logonuser)|呼叫這個方法來建立與指定的認證相關聯的使用者登入工作階段。|  
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|呼叫這個方法從 COM 伺服器，處理來自用戶端發出呼叫以初始化內`CAccessToken`COM 用戶端的存取權杖。|  
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|呼叫這個方法從伺服器中的製作要求透過具名管道來初始化`CAccessToken`從用戶端的存取權杖。|  
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|呼叫這個方法從伺服器處理 RPC 用戶端初始化的呼叫中`CAccessToken`從用戶端的存取權杖。|  
|[CAccessToken::OpenThreadToken](#openthreadtoken)|呼叫這個方法來設定模擬等級，然後初始化`CAccessToken`給定執行緒的權杖。|  
|[CAccessToken::PrivilegeCheck](#privilegecheck)|呼叫這個方法來判斷指定的權限集合中已啟用**CAccessToken**物件。|  
|[CAccessToken::Revert](#revert)|呼叫這個方法來停止的執行緒，使用模擬 token。|  
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|呼叫這個方法來設定預設的 DACL`CAccessToken`物件。|  
|[CAccessToken::SetOwner](#setowner)|呼叫這個方法來設定的擁有者`CAccessToken`物件。|  
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|呼叫這個方法來設定的主要群組`CAccessToken`物件。|  
  
## <a name="remarks"></a>備註  
 [存取權杖](http://msdn.microsoft.com/library/windows/desktop/aa374909)是一個物件，描述處理序或執行緒的安全性內容，並配置給每位使用者登入 Windows NT 或 Windows 2000 的系統。  
  
 在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h  
  
##  <a name="a-nameattacha--caccesstokenattach"></a><a name="attach"></a>CAccessToken::Attach  
 呼叫這個方法提供的存取權的語彙基元控制代碼的擁有權。  
  
```
void Attach(HANDLE hToken) throw();
```  
  
### <a name="parameters"></a>參數  
 *hToken*  
 存取權杖控制代碼。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`CAccessToken`物件已經有存取權杖的擁有權。  
  
##  <a name="a-namedtora--caccesstokencaccesstoken"></a><a name="dtor"></a>CAccessToken:: ~ CAccessToken  
 解構函式。  
  
```
virtual ~CAccessToken() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源。  
  
##  <a name="a-namechecktokenmembershipa--caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership  
 呼叫這個方法來判斷指定的 SID 是否已啟用在`CAccessToken`物件。  
  
```
bool CheckTokenMembership(
    const CSid& rSid, 
    bool* pbIsMember) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rSid`  
 若要參考[CSid 類別](../../atl/reference/csid-class.md)物件。  
  
 `pbIsMember`  
 指標，此變數會接收檢查的結果。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 `CheckTokenMembership`方法會檢查是否出現在使用者和群組 Sid 的存取權杖的 SID。 如果 SID，且具有 SE_GROUP_ENABLED 屬性*pbIsMember*是設定為 true，否則它會設定為 false。  
  
 在偵錯組建，判斷提示就會發生錯誤，如果`pbIsMember`不是有效的指標。  
  
> [!NOTE]
>  `CAccessToken`物件必須是模擬權杖，且不是主要的權杖。  
  
##  <a name="a-namecreateimpersonationtokena--caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken  
 呼叫這個方法來建立模擬存取權杖。  
  
```
bool CreateImpersonationToken(
    CAccessToken* pImp, 
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pImp`  
 新指標`CAccessToken`物件。  
  
 `sil`  
 指定[SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572)列舉型別，提供新的權杖模擬層級。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 `CreateImpersonationToken`呼叫[DuplicateToken](http://msdn.microsoft.com/library/windows/desktop/aa446616)來建立新的模擬語彙基元。  
  
##  <a name="a-namecreateprimarytokena--caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken  
 呼叫這個方法來建立新的主要權杖。  
  
```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pPri*  
 新指標`CAccessToken`物件。  
  
 `dwDesiredAccess`  
 指定新的權杖要求的存取權限。 預設值，MAXIMUM_ALLOWED，要求所有有效的呼叫端存取權限。 請參閱[存取權限和存取遮罩](http://msdn.microsoft.com/library/windows/desktop/aa374902)的更多的存取權限。  
  
 *pTokenAttributes*  
 指標[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)結構，指定新的權杖的安全性描述元，並且決定子處理序是否可以繼承語彙基元。 如果*pTokenAttributes*是 NULL、 語彙基元取得預設安全性描述元，且無法繼承控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 `CreatePrimaryToken`呼叫[DuplicateTokenEx](http://msdn.microsoft.com/library/windows/desktop/aa446617)來建立新的主要權杖。  
  
##  <a name="a-namecreateprocessasusera--caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a>CAccessToken::CreateProcessAsUser  
 呼叫這個方法來建立新的處理程序所表示的使用者安全性內容中執行`CAccessToken`物件。  
  
```
bool CreateProcessAsUser(
    LPCTSTR pApplicationName,
    LPTSTR pCommandLine,
    LPPROCESS_INFORMATION pProcessInformation,
    LPSTARTUPINFO pStartupInfo,
    DWORD dwCreationFlags = NORMAL_PRIORITY_CLASS,
    bool bLoadProfile = false,
    const CSecurityAttributes* pProcessAttributes = NULL,
    const CSecurityAttributes* pThreadAttributes = NULL,
    bool bInherit = false,
    LPCTSTR pCurrentDirectory = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 *pApplicationName*  
 以 null 終止的字串，指定要執行之模組的指標。 這個參數不可以是 NULL。  
  
 *pCommandLine*  
 以 null 終止的字串，指定要執行的命令列的指標。  
  
 *pProcessInformation*  
 指標[PROCESS_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/ms684873)收到新的處理序的識別資訊的結構。  
  
 *pStartupInfo*  
 指標[STARTUPINFO](http://msdn.microsoft.com/library/windows/desktop/ms686331)結構，指定新的處理序主視窗的顯示方式。  
  
 `dwCreationFlags`  
 指定控制優先順序類別和程序建立的其他旗標。 請參閱 Win32 函式[CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429)旗標的清單。  
  
 *bLoadProfile*  
 如果為 true，使用者的設定檔載入[LoadUserProfile](http://msdn.microsoft.com/library/windows/desktop/bb762281)。  
  
 *pProcessAttributes*  
 指標[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)結構，指定新的處理序的安全性描述元，並且決定子處理序是否可以繼承傳回的控制代碼。 如果*pProcessAttributes*是 NULL、 程序取得的預設安全性描述元，且無法繼承控制代碼。  
  
 *pThreadAttributes*  
 指標[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)結構，指定新的執行緒的安全性描述元，並且決定子處理序是否可以繼承傳回的控制代碼。 如果*pThreadAttributes*是 NULL，執行緒會取得預設安全性描述元，且無法繼承控制代碼。  
  
 *bInherit*  
 表示新的處理序是否會從呼叫處理序繼承控制代碼。 如果為 true，新的處理序都會繼承呼叫處理序中每個可繼承的開啟控制代碼。 繼承的控制代碼擁有相同的值和存取權限，原始的控制代碼的形式。  
  
 *pCurrentDirectory*  
 以 null 終止的字串，指定目前的磁碟機和目錄的新處理序的指標。 字串必須包含磁碟機代號的完整路徑。 如果這個參數是 NULL，新的處理序將擁有相同的目前磁碟機和目錄為呼叫處理序。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 **利用 CreateProcessAsUser**使用`CreateProcessAsUser`Win32 函式來建立新的處理序中所表示的使用者的安全性內容執行`CAccessToken`物件。 請參閱說明[CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429)函式的完整討論的所需的參數。  
  
 若要成功，這個方法`CAccessToken`（除非它是限制的權杖），物件必須保留 AssignPrimaryToken 和 IncreaseQuota 權限。  
  
##  <a name="a-namecreaterestrictedtokena--caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken  
 呼叫這個方法來建立新的限制`CAccessToken`物件。  
  
```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pRestrictedToken*  
 新的限制`CAccessToken`物件。  
  
 `SidsToDisable`  
 A`CTokenGroups`物件，指定禁用 Sid。  
  
 *SidsToRestrict*  
 A`CTokenGroups`指定限制 Sid 的物件。  
  
 `PrivilegesToDelete`  
 A`CTokenPrivileges`物件，指定要刪除權限限制的權杖中。 預設會建立一個空物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 `CreateRestrictedToken`使用[CreateRestrictedToken](http://msdn.microsoft.com/library/windows/desktop/aa446583) Win32 函式來建立新的`CAccessToken`物件，但有限制。  
  
> [!NOTE]
>  這個方法僅適用於 Windows 2000 或更新版本。  
  
> [!IMPORTANT]
>  當使用`CreateRestrictedToken`，請確認下列事項︰ 現有的權杖是有效的 （而且未由使用者輸入的） 和`SidsToDisable`和`PrivilegesToDelete`同時有效 （也無法由使用者輸入）。 如果方法傳回 false，則拒絕功能。  
  
##  <a name="a-namedetacha--caccesstokendetach"></a><a name="detach"></a>CAccessToken::Detach  
 呼叫這個方法，以撤銷存取權杖的擁有權。  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的控制代碼`CAccessToken`的已卸離。  
  
### <a name="remarks"></a>備註  
 這個方法會撤銷`CAccessToken`的存取權杖的擁有權。  
  
##  <a name="a-namedisableprivilegea--caccesstokendisableprivilege"></a><a name="disableprivilege"></a>CAccessToken::DisablePrivilege  
 呼叫這個方法，以停用中的權限`CAccessToken`物件。  
  
```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pszPrivilege`  
 字串，包含要在停用權限的指標`CAccessToken`物件。  
  
 `pPreviousState`  
 指標`CTokenPrivileges`物件將會包含先前狀態的權限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namedisableprivilegesa--caccesstokendisableprivileges"></a><a name="disableprivileges"></a>CAccessToken::DisablePrivileges  
 呼叫這個方法，以停用中的一個或多個權限`CAccessToken`物件。  
  
```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rPrivileges`  
 包含停用中的權限的字串陣列指標`CAccessToken`物件。  
  
 `pPreviousState`  
 指標`CTokenPrivileges`物件將會包含先前狀態的權限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-nameenableprivilegea--caccesstokenenableprivilege"></a><a name="enableprivilege"></a>CAccessToken::EnablePrivilege  
 呼叫這個方法來啟用的權限在`CAccessToken`物件。  
  
```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pszPrivilege`  
 字串，其中包含的權限，以便在指標`CAccessToken`物件。  
  
 `pPreviousState`  
 指標`CTokenPrivileges`物件將會包含先前狀態的權限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-nameenableprivilegesa--caccesstokenenableprivileges"></a><a name="enableprivileges"></a>CAccessToken::EnablePrivileges  
 呼叫這個方法來啟用中的一個或多個權限`CAccessToken`物件。  
  
```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rPrivileges`  
 陣列，包含啟用的權限的字串指標`CAccessToken`物件。  
  
 `pPreviousState`  
 指標`CTokenPrivileges`物件將會包含先前狀態的權限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namegetdefaultdacla--caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl  
 呼叫此方法以傳回`CAccessToken`物件的預設 DACL。  
  
```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pDacl`  
 指標[CDacl 類別](../../atl/reference/cdacl-class.md)物件將會收到**CAccessToken**物件的預設 DACL。  
  
### <a name="return-value"></a>傳回值  
 如果預設 DACL 已復原，則為 false 否則，就會傳回 true。  
  
##  <a name="a-namegeteffectivetokena--caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken  
 呼叫此方法來取得`CAccessToken`物件等於目前的執行緒作用中的存取權杖。  
  
```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwDesiredAccess`  
 指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namegetgroupsa--caccesstokengetgroups"></a><a name="getgroups"></a>CAccessToken::GetGroups  
 呼叫此方法以傳回`CAccessToken`物件的語彙基元的群組。  
  
```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pGroups*  
 指標[CTokenGroups 類別](../../atl/reference/ctokengroups-class.md)物件將會收到的群組資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namegethandlea--caccesstokengethandle"></a><a name="gethandle"></a>CAccessToken::GetHandle  
 呼叫這個方法來擷取存取權杖的處理常式。  
  
```
HANDLE GetHandle() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的控制代碼`CAccessToken`物件的存取權杖。  
  
##  <a name="a-namegetimpersonationlevela--caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel  
 呼叫這個方法來取得存取權杖中的模擬等級。  
  
```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pImpersonationLevel*  
 指標[SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572)列舉型別可接收的模擬層級資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namegetlogonsessionida--caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId  
 呼叫此方法以取得相關聯的登入工作階段識別碼`CAccessToken`物件。  
  
```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pluid`  
 指標[LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)這將會收到登入工作階段識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`pluid`是無效的值。  
  
##  <a name="a-namegetlogonsida--caccesstokengetlogonsid"></a><a name="getlogonsid"></a>CAccessToken::GetLogonSid  
 呼叫此方法以取得相關聯的登入 SID`CAccessToken`物件。  
  
```
bool GetLogonSid(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSid`  
 指標[CSid 類別](../../atl/reference/csid-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果*pSid*是無效的值。  
  
##  <a name="a-namegetownera--caccesstokengetowner"></a><a name="getowner"></a>CAccessToken::GetOwner  
 呼叫此方法以取得相關聯的擁有者`CAccessToken`物件。  
  
```
bool GetOwner(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSid`  
 指標[CSid 類別](../../atl/reference/csid-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 擁有者是由建立此存取權杖生效時的任何物件的預設設定。  
  
##  <a name="a-namegetprimarygroupa--caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a>CAccessToken::GetPrimaryGroup  
 呼叫此方法以取得相關聯的主要群組`CAccessToken`物件。  
  
```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSid`  
 指標[CSid 類別](../../atl/reference/csid-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 群組是由建立此存取權杖生效時的任何物件的預設設定。  
  
##  <a name="a-namegetprivilegesa--caccesstokengetprivileges"></a><a name="getprivileges"></a>CAccessToken::GetPrivileges  
 呼叫此方法以取得相關聯的權限`CAccessToken`物件。  
  
```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pPrivileges`  
 指標[CTokenPrivileges 類別](../../atl/reference/ctokenprivileges-class.md)要接收的權限的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namegetprocesstokena--caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a>CAccessToken::GetProcessToken  
 呼叫這個方法，以所指處理序的存取權杖初始化 `CAccessToken`。  
  
```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwDesiredAccess`  
 指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。  
  
 *hProcess*  
 處理已開啟存取權杖的處理序。 如果使用預設值 `NULL`，則會使用目前的處理序。  
  
### <a name="return-value"></a>傳回值  
 成功時傳回 `true`，失敗時則傳回 `false`。  
  
### <a name="remarks"></a>備註  
 呼叫[OpenProcessToken](http://msdn.microsoft.com/library/aa379295\(vs.85\).aspx) Win32 函式。  
  
##  <a name="a-namegetprofilea--caccesstokengetprofile"></a><a name="getprofile"></a>CAccessToken::GetProfile  
 呼叫此方法來取得指向 使用者設定檔相關聯的控制代碼`CAccessToken`物件。  
  
```
HANDLE GetProfile() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的控制代碼，如果沒有設定檔，指向使用者設定檔，則為 NULL。  
  
##  <a name="a-namegetsourcea--caccesstokengetsource"></a><a name="getsource"></a>CAccessToken::GetSource  
 呼叫此方法來取得來源的`CAccessToken`物件。  
  
```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pSource*  
 指標[TOKEN_SOURCE](http://msdn.microsoft.com/library/windows/desktop/aa379631)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namegetstatisticsa--caccesstokengetstatistics"></a><a name="getstatistics"></a>CAccessToken::GetStatistics  
 呼叫此方法以取得相關聯的資訊`CAccessToken`物件。  
  
```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pStatistics*  
 指標[TOKEN_STATISTICS](http://msdn.microsoft.com/library/windows/desktop/aa379632)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namegetterminalservicessessionida--caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId  
 呼叫此方法以取得相關聯的終端機服務工作階段識別碼`CAccessToken`物件。  
  
```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pdwSessionId*  
 終端機服務工作階段識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namegetthreadtokena--caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a>CAccessToken::GetThreadToken  
 呼叫此方法以初始化`CAccessToken`給定執行緒的權杖。  
  
```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwDesiredAccess`  
 指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。  
  
 `hThread`  
 在開啟存取權杖的執行緒控制代碼。  
  
 `bOpenAsSelf`  
 指出是否針對執行緒呼叫的安全性內容進行存取檢查`GetThreadToken`方法對呼叫端執行緒的程序的安全性內容。  
  
 如果此參數為 false，會執行存取檢查，使用呼叫執行緒的安全性內容。 如果執行緒模擬用戶端，此安全性內容可能是用戶端處理序。 如果此參數為 true，是使用的安全性內容的程序呼叫的執行緒在進行存取檢查。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namegettokenida--caccesstokengettokenid"></a><a name="gettokenid"></a>CAccessToken::GetTokenId  
 呼叫此方法以取得相關聯的語彙基元 ID`CAccessToken`物件。  
  
```
bool GetTokenId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pluid`  
 指標[LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)這將會收到權杖的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namegettypea--caccesstokengettype"></a><a name="gettype"></a>CAccessToken::GetType  
 呼叫這個方法來取得的權杖類型`CAccessToken`物件。  
  
```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pType`  
 位址[TOKEN_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379633) ，成功時，收到的權杖類型的變數。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 **TOKEN_TYPE**列舉型別包含區分主要權杖與模擬語彙基元的值。  
  
##  <a name="a-namegetusera--caccesstokengetuser"></a><a name="getuser"></a>CAccessToken::GetUser  
 呼叫這個方法來識別相關聯的使用者`CAccessToken`物件。  
  
```
bool GetUser(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSid`  
 指標[CSid 類別](../../atl/reference/csid-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="a-namehkeycurrentusera--caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser  
 呼叫此方法來取得指向 使用者設定檔相關聯的控制代碼`CAccessToken`物件。  
  
```
HKEY HKeyCurrentUser() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的控制代碼，如果沒有設定檔，指向使用者設定檔，則為 NULL。  
  
##  <a name="a-nameimpersonatea--caccesstokenimpersonate"></a><a name="impersonate"></a>CAccessToken::Impersonate  
 呼叫這個方法來指派模擬`CAccessToken`到往來文章。  
  
```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `hThread`  
 執行緒指派模擬語彙基元的控制代碼。 這個控制代碼必須已經開啟的 TOKEN_IMPERSONATE 存取權限。 如果`hThread`是 NULL，此方法會造成執行緒停止使用模擬 token。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`CAccessToken`沒有有效的語彙基元指標。  
  
 [CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖。  
  
##  <a name="a-nameimpersonateloggedonusera--caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a>CAccessToken::ImpersonateLoggedOnUser  
 呼叫此方法可讓呼叫的執行緒來模擬登入之使用者的安全性內容。  
  
```
bool ImpersonateLoggedOnUser() const throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  如果模擬函式的呼叫失敗，因為任何原因，無法模擬用戶端，並從中進行呼叫的程序的安全性內容中建立用戶端要求。 如果處理程序正在執行做為高特殊權限的帳戶，或以系統管理群組的成員，使用者可能可以執行的動作他或她就否則不允許。 因此，應該一律確認此函式的傳回值。  
  
##  <a name="a-nameistokenrestricteda--caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted  
 呼叫這個方法來測試是否`CAccessToken`物件包含一份 Sid 限制。  
  
```
bool IsTokenRestricted() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件包含限制 Sid，false，如果不有任何限制 Sid 的清單，或如果方法失敗，則傳回 true。  
  
##  <a name="a-nameloaduserprofilea--caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a>CAccessToken::LoadUserProfile  
 呼叫這個方法來載入使用者設定檔相關聯`CAccessToken`物件。  
  
```
bool LoadUserProfile() throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`CAccessToken`未包含有效的語彙基元，或是如果使用者設定檔已經存在。  
  
##  <a name="a-namelogonusera--caccesstokenlogonuser"></a><a name="logonuser"></a>CAccessToken::LogonUser  
 呼叫這個方法來建立與指定的認證相關聯的使用者登入工作階段。  
  
```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszUserName`  
 以 null 終止的字串，指定使用者名稱的指標。 這是登入的使用者帳戶的名稱。  
  
 *pszDomain*  
 以 null 終止的字串，指定的網域或其帳戶資料庫內的伺服器名稱的指標`pszUserName`帳戶。  
  
 `pszPassword`  
 以 null 終止的字串，指定所指定的使用者帳戶的純文字密碼的指標`pszUserName`。  
  
 *dwLogonType*  
 指定要執行的登入作業的類型。 請參閱[LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184)如需詳細資訊。  
  
 *dwLogonProvider*  
 指定登入提供者。 請參閱[LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184)如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 將相關聯的登入的語彙基元所產生的存取權`CAccessToken`。 若要成功，這個方法`CAccessToken`物件必須保留 SE_TCB_NAME 權限持有者識別做為基底的受信任電腦的一部分。 請參閱[LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184)有關所需的權限。  
  
##  <a name="a-nameopencomclienttokena--caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken  
 呼叫這個方法從 COM 伺服器，處理來自用戶端發出呼叫以初始化內`CAccessToken`COM 用戶端的存取權杖。  
  
```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `dwDesiredAccess`  
 指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。  
  
 `bImpersonate`  
 如果為 true，目前的執行緒會模擬呼叫的 COM 用戶端，即使已成功完成此呼叫。 如果為 false，將會開啟存取權杖，但執行緒並不會模擬語彙基元這個呼叫完成時。  
  
 `bOpenAsSelf`  
 指出是否針對執行緒呼叫的安全性內容進行存取檢查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法對呼叫端執行緒的程序的安全性內容。  
  
 如果此參數為 false，會執行存取檢查，使用呼叫執行緒的安全性內容。 如果執行緒模擬用戶端，此安全性內容可能是用戶端處理序。 如果此參數為 true，是使用的安全性內容的程序呼叫的執行緒在進行存取檢查。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 [CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖來建立`bImpersonate`旗標設為*true*。  
  
##  <a name="a-nameopennamedpipeclienttokena--caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken  
 呼叫這個方法從伺服器中的製作要求透過具名管道來初始化`CAccessToken`從用戶端的存取權杖。  
  
```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>參數  
 *hPipe*  
 具名管道的控制代碼。  
  
 `dwDesiredAccess`  
 指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。  
  
 `bImpersonate`  
 如果為 true，目前的執行緒會模擬呼叫管道用戶端，即使已成功完成此呼叫。 如果為 false，將會開啟存取權杖，但執行緒並不會模擬語彙基元這個呼叫完成時。  
  
 `bOpenAsSelf`  
 指出是否針對執行緒呼叫的安全性內容進行存取檢查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法對呼叫端執行緒的程序的安全性內容。  
  
 如果此參數為 false，會執行存取檢查，使用呼叫執行緒的安全性內容。 如果執行緒模擬用戶端，此安全性內容可能是用戶端處理序。 如果此參數為 true，是使用的安全性內容的程序呼叫的執行緒在進行存取檢查。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 [CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖來建立`bImpersonate`旗標設為*true*。  
  
##  <a name="a-nameopenrpcclienttokena--caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken  
 呼叫這個方法從伺服器處理 RPC 用戶端初始化的呼叫中`CAccessToken`從用戶端的存取權杖。  
  
```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>參數  
 *BindingHandle*  
 表示用戶端的繫結的伺服器上的控制代碼繫結。  
  
 `dwDesiredAccess`  
 指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。  
  
 `bImpersonate`  
 如果為 true，目前的執行緒會模擬呼叫的 RPC 用戶端，即使已成功完成此呼叫。 如果為 false，將會開啟存取權杖，但執行緒並不會模擬語彙基元這個呼叫完成時。  
  
 `bOpenAsSelf`  
 指出是否針對執行緒呼叫的安全性內容進行存取檢查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法對呼叫端執行緒的程序的安全性內容。  
  
 如果此參數為 false，會執行存取檢查，使用呼叫執行緒的安全性內容。 如果執行緒模擬用戶端，此安全性內容可能是用戶端處理序。 如果此參數為 true，是使用的安全性內容的程序呼叫的執行緒在進行存取檢查。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 [CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖來建立`bImpersonate`旗標設為*true*。  
  
##  <a name="a-nameopenthreadtokena--caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a>CAccessToken::OpenThreadToken  
 呼叫這個方法來設定模擬等級，然後初始化`CAccessToken`給定執行緒的權杖。  
  
```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `dwDesiredAccess`  
 指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。  
  
 `bImpersonate`  
 如果為 true，執行緒會保留在要求的模擬層級，這個方法完成之後。 如果為 false，執行緒將會還原為其原始的模擬層級。  
  
 `bOpenAsSelf`  
 指出是否針對執行緒呼叫的安全性內容進行存取檢查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法對呼叫端執行緒的程序的安全性內容。  
  
 如果此參數為 false，會執行存取檢查，使用呼叫執行緒的安全性內容。 如果執行緒模擬用戶端，此安全性內容可能是用戶端處理序。 如果此參數為 true，是使用的安全性內容的程序呼叫的執行緒在進行存取檢查。  
  
 `sil`  
 指定[SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572)列舉型別提供的語彙基元的模擬等級。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 `OpenThreadToken`類似於[CAccessToken::GetThreadToken](#getthreadtoken)，但初始化之前設定的模擬等級`CAccessToken`從執行緒的存取權杖。  
  
 [CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖來建立`bImpersonate`旗標設為*true*。  
  
##  <a name="a-nameprivilegechecka--caccesstokenprivilegecheck"></a><a name="privilegecheck"></a>CAccessToken::PrivilegeCheck  
 呼叫這個方法來判斷指定的權限集合中已啟用**CAccessToken**物件。  
  
```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
     bool* pbResult) const throw();
```  
  
### <a name="parameters"></a>參數  
 *[Requiredprivileges]*  
 指標[PRIVILEGE_SET](http://msdn.microsoft.com/library/windows/desktop/aa379307)結構。  
  
 *pbResult*  
 值指標的方法會設定指出是否啟用任何或所有指定的權限在`CAccessToken`物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 當`PrivilegeCheck`傳回，**屬性**的每個成員[LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)結構設 SE_PRIVILEGE_USED_FOR_ACCESS，如果已啟用對應的權限。 這個方法會呼叫[PrivilegeCheck](http://msdn.microsoft.com/library/windows/desktop/aa379304) Win32 函式。  
  
##  <a name="a-namereverta--caccesstokenrevert"></a><a name="revert"></a>CAccessToken::Revert  
 呼叫這個方法來停止使用模擬語彙基元的執行緒。  
  
```
bool Revert(HANDLE hThread = NULL) const throw();
```  
  
### <a name="parameters"></a>參數  
 `hThread`  
 若要還原的模擬執行緒的控制代碼。 如果*hThread*是 NULL 時，會假設目前的執行緒。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 可以自動執行的模擬語彙基元回復，與[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)。  
  
##  <a name="a-namesetdefaultdacla--caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl  
 呼叫這個方法來設定預設的 DACL`CAccessToken`物件。  
  
```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rDacl`  
 新的預設值[CDacl 類別](../../atl/reference/cdacl-class.md)資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 預設 DACL，為新物件作用中建立與此存取權杖時，會使用預設的 DACL。  
  
##  <a name="a-namesetownera--caccesstokensetowner"></a><a name="setowner"></a>CAccessToken::SetOwner  
 呼叫這個方法來設定的擁有者`CAccessToken`物件。  
  
```
bool SetOwner(const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rSid`  
 [CSid 類別](../../atl/reference/csid-class.md)物件，其中包含擁有者資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 擁有者是用於建立此存取權杖生效時的新物件的預設擁有者。  
  
##  <a name="a-namesetprimarygroupa--caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup  
 呼叫這個方法來設定的主要群組`CAccessToken`物件。  
  
```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rSid`  
 [CSid 類別](../../atl/reference/csid-class.md)物件，其中包含的主要群組資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 主要群組是此存取權杖生效時所建立的新物件的預設群組。  
  
## <a name="see-also"></a>另請參閱  
 [ATLSecurity 範例](../../visual-cpp-samples.md)   
 [存取權杖](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [類別概觀](../../atl/atl-class-overview.md)

