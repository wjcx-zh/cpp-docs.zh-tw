---
title: CAccessToken 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAccessToken
- ATLSECURITY/ATL::CAccessToken
- ATLSECURITY/ATL::CAccessToken::Attach
- ATLSECURITY/ATL::CAccessToken::CheckTokenMembership
- ATLSECURITY/ATL::CAccessToken::CreateImpersonationToken
- ATLSECURITY/ATL::CAccessToken::CreatePrimaryToken
- ATLSECURITY/ATL::CAccessToken::CreateProcessAsUser
- ATLSECURITY/ATL::CAccessToken::CreateRestrictedToken
- ATLSECURITY/ATL::CAccessToken::Detach
- ATLSECURITY/ATL::CAccessToken::DisablePrivilege
- ATLSECURITY/ATL::CAccessToken::DisablePrivileges
- ATLSECURITY/ATL::CAccessToken::EnablePrivilege
- ATLSECURITY/ATL::CAccessToken::EnablePrivileges
- ATLSECURITY/ATL::CAccessToken::GetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::GetEffectiveToken
- ATLSECURITY/ATL::CAccessToken::GetGroups
- ATLSECURITY/ATL::CAccessToken::GetHandle
- ATLSECURITY/ATL::CAccessToken::GetImpersonationLevel
- ATLSECURITY/ATL::CAccessToken::GetLogonSessionId
- ATLSECURITY/ATL::CAccessToken::GetLogonSid
- ATLSECURITY/ATL::CAccessToken::GetOwner
- ATLSECURITY/ATL::CAccessToken::GetPrimaryGroup
- ATLSECURITY/ATL::CAccessToken::GetPrivileges
- ATLSECURITY/ATL::CAccessToken::GetProcessToken
- ATLSECURITY/ATL::CAccessToken::GetProfile
- ATLSECURITY/ATL::CAccessToken::GetSource
- ATLSECURITY/ATL::CAccessToken::GetStatistics
- ATLSECURITY/ATL::CAccessToken::GetTerminalServicesSessionId
- ATLSECURITY/ATL::CAccessToken::GetThreadToken
- ATLSECURITY/ATL::CAccessToken::GetTokenId
- ATLSECURITY/ATL::CAccessToken::GetType
- ATLSECURITY/ATL::CAccessToken::GetUser
- ATLSECURITY/ATL::CAccessToken::HKeyCurrentUser
- ATLSECURITY/ATL::CAccessToken::Impersonate
- ATLSECURITY/ATL::CAccessToken::ImpersonateLoggedOnUser
- ATLSECURITY/ATL::CAccessToken::IsTokenRestricted
- ATLSECURITY/ATL::CAccessToken::LoadUserProfile
- ATLSECURITY/ATL::CAccessToken::LogonUser
- ATLSECURITY/ATL::CAccessToken::OpenCOMClientToken
- ATLSECURITY/ATL::CAccessToken::OpenNamedPipeClientToken
- ATLSECURITY/ATL::CAccessToken::OpenRPCClientToken
- ATLSECURITY/ATL::CAccessToken::OpenThreadToken
- ATLSECURITY/ATL::CAccessToken::PrivilegeCheck
- ATLSECURITY/ATL::CAccessToken::Revert
- ATLSECURITY/ATL::CAccessToken::SetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::SetOwner
- ATLSECURITY/ATL::CAccessToken::SetPrimaryGroup
dev_langs:
- C++
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 407652cc5a5e300a2e5eb9d6a5a07dd29209ffef
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366337"
---
# <a name="caccesstoken-class"></a>CAccessToken 類別
這個類別是存取權杖的包裝函式。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAccessToken
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAccessToken::~CAccessToken](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAccessToken::Attach](#attach)|呼叫此方法以取得指定的存取語彙基元的控制代碼的擁有權。|  
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|呼叫此方法以判斷指定的 SID 是否已啟用在`CAccessToken`物件。|  
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|呼叫此方法以建立新的模擬存取權杖。|  
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|呼叫此方法以建立新的主要權杖。|  
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|呼叫此方法以建立新的處理程序所表示的使用者安全性內容中執行`CAccessToken`物件。|  
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|呼叫此方法以建立新的限制`CAccessToken`物件。|  
|[CAccessToken::Detach](#detach)|呼叫這個方法，以撤銷存取權杖的擁有權。|  
|[CAccessToken::DisablePrivilege](#disableprivilege)|呼叫此方法以停用中的權限`CAccessToken`物件。|  
|[CAccessToken::DisablePrivileges](#disableprivileges)|呼叫此方法以停用中的一個或多個權限`CAccessToken`物件。|  
|[CAccessToken::EnablePrivilege](#enableprivilege)|呼叫此方法以啟用中的權限`CAccessToken`物件。|  
|[CAccessToken::EnablePrivileges](#enableprivileges)|呼叫此方法以啟用中的一個或多個權限`CAccessToken`物件。|  
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|呼叫此方法以傳回`CAccessToken`物件的預設 DACL。|  
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|呼叫此方法來取得`CAccessToken`物件等於目前的執行緒作用中的存取權杖。|  
|[CAccessToken::GetGroups](#getgroups)|呼叫此方法以傳回`CAccessToken`物件的語彙基元的群組。|  
|[CAccessToken::GetHandle](#gethandle)|呼叫此方法以擷取存取權杖的控制代碼。|  
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|呼叫這個方法，取得存取權杖中的模擬等級。|  
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|呼叫此方法以取得相關聯的登入工作階段識別碼`CAccessToken`物件。|  
|[CAccessToken::GetLogonSid](#getlogonsid)|呼叫此方法以取得相關聯的登入 SID`CAccessToken`物件。|  
|[CAccessToken::GetOwner](#getowner)|呼叫此方法以取得相關聯的擁有者`CAccessToken`物件。|  
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|呼叫此方法以取得相關聯的主要群組`CAccessToken`物件。|  
|[CAccessToken::GetPrivileges](#getprivileges)|呼叫此方法以取得相關聯的權限`CAccessToken`物件。|  
|[CAccessToken::GetProcessToken](#getprocesstoken)|呼叫這個方法，以所指處理序的存取權杖初始化 `CAccessToken`。|  
|[CAccessToken::GetProfile](#getprofile)|呼叫此方法來取得指向相關聯的使用者設定檔的控制代碼`CAccessToken`物件。|  
|[CAccessToken::GetSource](#getsource)|呼叫這個方法來取得的來源`CAccessToken`物件。|  
|[CAccessToken::GetStatistics](#getstatistics)|呼叫此方法以取得相關聯的資訊`CAccessToken`物件。|  
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|呼叫此方法以取得相關聯的終端機服務工作階段識別碼`CAccessToken`物件。|  
|[CAccessToken::GetThreadToken](#getthreadtoken)|呼叫此方法以初始化`CAccessToken`給定執行緒的權杖。|  
|[CAccessToken::GetTokenId](#gettokenid)|呼叫此方法以取得相關聯的語彙基元識別碼`CAccessToken`物件。|  
|[CAccessToken::GetType](#gettype)|呼叫此方法來取得權杖的型別`CAccessToken`物件。|  
|[CAccessToken::GetUser](#getuser)|呼叫這個方法來識別相關聯的使用者`CAccessToken`物件。|  
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|呼叫此方法來取得指向相關聯的使用者設定檔的控制代碼`CAccessToken`物件。|  
|[CAccessToken::Impersonate](#impersonate)|呼叫這個方法來指派模擬`CAccessToken`執行緒。|  
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|呼叫此方法可讓呼叫執行緒模擬登入之使用者的安全性內容。|  
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|呼叫此方法以測試是否`CAccessToken`物件包含一份受限制的 Sid。|  
|[CAccessToken::LoadUserProfile](#loaduserprofile)|呼叫此方法以載入使用者設定檔相關聯`CAccessToken`物件。|  
|[CAccessToken::LogonUser](#logonuser)|呼叫這個方法來建立與給定認證相關聯之使用者的登入工作階段。|  
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|中呼叫這個方法從 COM 伺服器在處理來自用戶端呼叫以初始化`CAccessToken`COM 用戶端的存取權杖。|  
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|中呼叫這個方法從伺服器擷取要求透過具名管道來初始化`CAccessToken`從用戶端的存取權杖。|  
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|呼叫這個方法從伺服器處理 RPC 用戶端對初始化的呼叫中`CAccessToken`從用戶端的存取權杖。|  
|[CAccessToken::OpenThreadToken](#openthreadtoken)|呼叫這個方法來設定模擬等級，然後初始化`CAccessToken`給定執行緒的權杖。|  
|[CAccessToken::PrivilegeCheck](#privilegecheck)|呼叫此方法以判斷指定的權限集合中已啟用**CAccessToken**物件。|  
|[CAccessToken::Revert](#revert)|呼叫這個方法來停止的執行緒，使用模擬語彙基元。|  
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|呼叫此方法以設定預設的 DACL`CAccessToken`物件。|  
|[CAccessToken::SetOwner](#setowner)|呼叫此方法以設定的擁有者`CAccessToken`物件。|  
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|呼叫此方法以設定的主要群組`CAccessToken`物件。|  
  
## <a name="remarks"></a>備註  
 [存取權杖](http://msdn.microsoft.com/library/windows/desktop/aa374909)是描述程序或執行緒的安全性內容，並配置給每位使用者登入 Windows 系統的物件。  
  
 如需在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)Windows SDK 中。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsecurity.h  
  
##  <a name="attach"></a>  CAccessToken::Attach  
 呼叫此方法以取得指定的存取語彙基元的控制代碼的擁有權。  
  
```
void Attach(HANDLE hToken) throw();
```  
  
### <a name="parameters"></a>參數  
 *hToken*  
 存取語彙基元控制代碼。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`CAccessToken`物件已經有一個存取權杖的擁有權。  
  
##  <a name="dtor"></a>  CAccessToken::~CAccessToken  
 解構函式。  
  
```
virtual ~CAccessToken() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源。  
  
##  <a name="checktokenmembership"></a>  CAccessToken::CheckTokenMembership  
 呼叫此方法以判斷指定的 SID 是否已啟用在`CAccessToken`物件。  
  
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
 `CheckTokenMembership`方法會檢查是否有在使用者和群組 Sid 的存取權杖的 SID。 如果 SID 存在，並且具有 SE_GROUP_ENABLED 屬性*pbIsMember*是設定為 true，否則它設定為 false。  
  
 在偵錯組建，判斷提示就會發生錯誤，如果`pbIsMember`不是有效的指標。  
  
> [!NOTE]
>  `CAccessToken`物件必須是模擬權杖，且不是主要的權杖。  
  
##  <a name="createimpersonationtoken"></a>  CAccessToken::CreateImpersonationToken  
 呼叫此方法以建立模擬存取權杖。  
  
```
bool CreateImpersonationToken(
    CAccessToken* pImp, 
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pImp`  
 新的指標`CAccessToken`物件。  
  
 `sil`  
 指定[SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572)列舉型別，提供新的權杖模擬層級。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 `CreateImpersonationToken` 呼叫[DuplicateToken](http://msdn.microsoft.com/library/windows/desktop/aa446616)以建立新的模擬權杖。  
  
##  <a name="createprimarytoken"></a>  CAccessToken::CreatePrimaryToken  
 呼叫此方法以建立新的主要權杖。  
  
```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pPri*  
 新的指標`CAccessToken`物件。  
  
 `dwDesiredAccess`  
 指定新的權杖要求的存取權限。 預設值，MAXIMUM_ALLOWED，要求所有呼叫端的有效存取權限。 請參閱[存取權限和存取遮罩](http://msdn.microsoft.com/library/windows/desktop/aa374902)的更多的存取權限。  
  
 *pTokenAttributes*  
 指標[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)結構，指定新的權杖的安全性描述元，並且決定子處理序是否可以繼承語彙基元。 如果*pTokenAttributes*是 NULL，語彙基元，取得預設安全性描述元，而且無法繼承控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 `CreatePrimaryToken` 呼叫[DuplicateTokenEx](http://msdn.microsoft.com/library/windows/desktop/aa446617)以建立新的主要權杖。  
  
##  <a name="createprocessasuser"></a>  CAccessToken::CreateProcessAsUser  
 呼叫此方法以建立新的處理程序所表示的使用者安全性內容中執行`CAccessToken`物件。  
  
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
 指標[PROCESS_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/ms684873)接收新的處理序的識別資訊的結構。  
  
 *pStartupInfo*  
 指標[STARTUPINFO](http://msdn.microsoft.com/library/windows/desktop/ms686331)結構，指定新的處理序主視窗的顯示方式。  
  
 `dwCreationFlags`  
 指定控制的優先權等級的程序建立的額外旗標。 請參閱 Win32 函式[CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429)旗標的清單。  
  
 *bLoadProfile*  
 如果為 true，使用者的設定檔載入[LoadUserProfile](http://msdn.microsoft.com/library/windows/desktop/bb762281)。  
  
 *pProcessAttributes*  
 指標[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)結構，指定新的處理序的安全性描述元，並且決定子處理序是否可以繼承傳回的控制代碼。 如果*pProcessAttributes*是 NULL，此程序取得預設安全性描述元，而且無法繼承控制代碼。  
  
 *pThreadAttributes*  
 指標[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)結構，指定新的執行緒的安全性描述元，並且決定子處理序是否可以繼承傳回的控制代碼。 如果*pThreadAttributes*是 NULL，則執行緒會取得預設安全性描述元，而且無法繼承控制代碼。  
  
 *bInherit*  
 表示新處理序是否會從呼叫處理序繼承控制代碼。 如果為 true，新處理序都會繼承呼叫處理序中每個繼承的開啟控制代碼。 繼承的控制代碼具有相同的值和存取權限，原始的控制代碼的形式。  
  
 *pCurrentDirectory*  
 以 null 終止的字串，指定目前的磁碟機和目錄的新處理序的指標。 字串必須包含磁碟機代號的完整路徑。 如果這個參數是 NULL，新處理序必須相同目前的磁碟機和目錄做為呼叫處理序。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 **CreateProcessAsUser**使用`CreateProcessAsUser`Win32 函式來建立新的處理序中所表示的使用者的安全性內容執行`CAccessToken`物件。 請參閱描述[CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429)函式的完整討論內容所需的參數。  
  
 若要成功，這個方法`CAccessToken`物件必須保留 AssignPrimaryToken （除非它是受限制的權杖） 和 IncreaseQuota 權限。  
  
##  <a name="createrestrictedtoken"></a>  CAccessToken::CreateRestrictedToken  
 呼叫此方法以建立新的限制`CAccessToken`物件。  
  
```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pRestrictedToken*  
 新限制`CAccessToken`物件。  
  
 `SidsToDisable`  
 A`CTokenGroups`物件，指定禁用 Sid。  
  
 *SidsToRestrict*  
 A`CTokenGroups`物件，指定限制的 Sid。  
  
 `PrivilegesToDelete`  
 A`CTokenPrivileges`物件，指定要刪除權限受限制的權杖中。 預設會建立空的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 `CreateRestrictedToken` 使用[CreateRestrictedToken](http://msdn.microsoft.com/library/windows/desktop/aa446583) Win32 函式，建立新`CAccessToken`物件，但有限制。  
  
> [!IMPORTANT]
>  當使用`CreateRestrictedToken`，請先確定以下： 現有的語彙基元是有效的 （而不輸入使用者的） 和`SidsToDisable`和`PrivilegesToDelete`都有效 （而不由使用者輸入）。 方法會傳回 false，如果拒絕功能。  
  
##  <a name="detach"></a>  CAccessToken::Detach  
 呼叫這個方法，以撤銷存取權杖的擁有權。  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的控制代碼`CAccessToken`的已卸離。  
  
### <a name="remarks"></a>備註  
 這個方法會撤銷`CAccessToken`的存取權杖的擁有權。  
  
##  <a name="disableprivilege"></a>  CAccessToken::DisablePrivilege  
 呼叫此方法以停用中的權限`CAccessToken`物件。  
  
```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pszPrivilege`  
 字串，包含的特殊權限，以停用指標`CAccessToken`物件。  
  
 `pPreviousState`  
 指標`CTokenPrivileges`物件將會包含先前狀態的權限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="disableprivileges"></a>  CAccessToken::DisablePrivileges  
 呼叫此方法以停用中的一個或多個權限`CAccessToken`物件。  
  
```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rPrivileges`  
 包含要在停用的權限的字串陣列指標`CAccessToken`物件。  
  
 `pPreviousState`  
 指標`CTokenPrivileges`物件將會包含先前狀態的權限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="enableprivilege"></a>  CAccessToken::EnablePrivilege  
 呼叫此方法以啟用中的權限`CAccessToken`物件。  
  
```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pszPrivilege`  
 字串，包含在中啟用的權限的指標`CAccessToken`物件。  
  
 `pPreviousState`  
 指標`CTokenPrivileges`物件將會包含先前狀態的權限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="enableprivileges"></a>  CAccessToken::EnablePrivileges  
 呼叫此方法以啟用中的一個或多個權限`CAccessToken`物件。  
  
```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rPrivileges`  
 包含在中啟用的權限的字串陣列指標`CAccessToken`物件。  
  
 `pPreviousState`  
 指標`CTokenPrivileges`物件將會包含先前狀態的權限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="getdefaultdacl"></a>  CAccessToken::GetDefaultDacl  
 呼叫此方法以傳回`CAccessToken`物件的預設 DACL。  
  
```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pDacl`  
 指標[CDacl 類別](../../atl/reference/cdacl-class.md)物件將會接收**CAccessToken**物件的預設 DACL。  
  
### <a name="return-value"></a>傳回值  
 如果預設 DACL 已復原，false。 否則，就會傳回 true。  
  
##  <a name="geteffectivetoken"></a>  CAccessToken::GetEffectiveToken  
 呼叫此方法來取得`CAccessToken`物件等於目前的執行緒作用中的存取權杖。  
  
```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwDesiredAccess`  
 指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="getgroups"></a>  CAccessToken::GetGroups  
 呼叫此方法以傳回`CAccessToken`物件的語彙基元的群組。  
  
```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pGroups*  
 指標[CTokenGroups 類別](../../atl/reference/ctokengroups-class.md)物件將會接收的群組資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="gethandle"></a>  CAccessToken::GetHandle  
 呼叫此方法以擷取存取權杖的控制代碼。  
  
```
HANDLE GetHandle() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的控制代碼`CAccessToken`物件的存取權杖。  
  
##  <a name="getimpersonationlevel"></a>  CAccessToken::GetImpersonationLevel  
 呼叫這個方法，取得存取權杖中的模擬等級。  
  
```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pImpersonationLevel*  
 指標[SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572)列舉型別將會接收的模擬層級資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="getlogonsessionid"></a>  CAccessToken::GetLogonSessionId  
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
  
##  <a name="getlogonsid"></a>  CAccessToken::GetLogonSid  
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
  
##  <a name="getowner"></a>  CAccessToken::GetOwner  
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
 擁有者是由建立此存取權杖生效時的任何物件上的預設設定。  
  
##  <a name="getprimarygroup"></a>  CAccessToken::GetPrimaryGroup  
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
 建立此存取權杖生效時的任何物件上的預設設定群組。  
  
##  <a name="getprivileges"></a>  CAccessToken::GetPrivileges  
 呼叫此方法以取得相關聯的權限`CAccessToken`物件。  
  
```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pPrivileges`  
 指標[CTokenPrivileges 類別](../../atl/reference/ctokenprivileges-class.md)會獲得的權限的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="getprocesstoken"></a>  CAccessToken::GetProcessToken  
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
  
##  <a name="getprofile"></a>  CAccessToken::GetProfile  
 呼叫此方法來取得指向相關聯的使用者設定檔的控制代碼`CAccessToken`物件。  
  
```
HANDLE GetProfile() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的控制代碼，如果沒有設定檔，指向的使用者設定檔或為 NULL。  
  
##  <a name="getsource"></a>  CAccessToken::GetSource  
 呼叫這個方法來取得的來源`CAccessToken`物件。  
  
```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pSource*  
 指標[TOKEN_SOURCE](http://msdn.microsoft.com/library/windows/desktop/aa379631)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="getstatistics"></a>  CAccessToken::GetStatistics  
 呼叫此方法以取得相關聯的資訊`CAccessToken`物件。  
  
```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pStatistics*  
 指標[TOKEN_STATISTICS](http://msdn.microsoft.com/library/windows/desktop/aa379632)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="getterminalservicessessionid"></a>  CAccessToken::GetTerminalServicesSessionId  
 呼叫此方法以取得相關聯的終端機服務工作階段識別碼`CAccessToken`物件。  
  
```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pdwSessionId*  
 終端機服務工作階段識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="getthreadtoken"></a>  CAccessToken::GetThreadToken  
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
 執行緒的存取語彙基元開啟的控制代碼。  
  
 `bOpenAsSelf`  
 指出是否要對執行緒呼叫的安全性內容的存取檢查`GetThreadToken`方法或對呼叫端執行緒的程序的安全性內容。  
  
 如果此參數為 false，使用安全性內容來執行呼叫的執行緒執行存取檢查。 如果執行緒正在模擬用戶端，可以是此安全性內容的用戶端處理序。 此參數為 true，如果使用的安全性內容的程序呼叫的執行緒進行存取檢查。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="gettokenid"></a>  CAccessToken::GetTokenId  
 呼叫此方法以取得相關聯的語彙基元識別碼`CAccessToken`物件。  
  
```
bool GetTokenId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pluid`  
 指標[LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)這將會收到語彙基元的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="gettype"></a>  CAccessToken::GetType  
 呼叫此方法來取得權杖的型別`CAccessToken`物件。  
  
```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pType`  
 位址[TOKEN_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379633) ，成功時，接收變數的語彙基元的類型。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 **TOKEN_TYPE**列舉型別包含區分的主要權杖與模擬語彙基元之間的值。  
  
##  <a name="getuser"></a>  CAccessToken::GetUser  
 呼叫這個方法來識別相關聯的使用者`CAccessToken`物件。  
  
```
bool GetUser(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSid`  
 指標[CSid 類別](../../atl/reference/csid-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
##  <a name="hkeycurrentuser"></a>  CAccessToken::HKeyCurrentUser  
 呼叫此方法來取得指向相關聯的使用者設定檔的控制代碼`CAccessToken`物件。  
  
```
HKEY HKeyCurrentUser() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的控制代碼，如果沒有設定檔，指向的使用者設定檔或為 NULL。  
  
##  <a name="impersonate"></a>  CAccessToken::Impersonate  
 呼叫這個方法來指派模擬`CAccessToken`執行緒。  
  
```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `hThread`  
 執行緒指派模擬語彙基元的控制代碼。 這個控制代碼必須開啟使用 TOKEN_IMPERSONATE 存取權限。 如果`hThread`是 NULL，方法會造成執行緒停止使用模擬語彙基元。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`CAccessToken`沒有有效的語彙基元指標。  
  
 [CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖。  
  
##  <a name="impersonateloggedonuser"></a>  CAccessToken::ImpersonateLoggedOnUser  
 呼叫此方法可讓呼叫執行緒模擬登入之使用者的安全性內容。  
  
```
bool ImpersonateLoggedOnUser() const throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  如果模擬函式的呼叫失敗，因為任何原因，無法模擬該用戶端，並從中進行呼叫的程序的安全性內容中進行用戶端要求。 如果處理序正在執行做為高特殊權限的帳戶，或做為管理群組的成員，使用者可能可以執行動作他或她會否則不允許。 因此，應該一律確認此函式的傳回值。  
  
##  <a name="istokenrestricted"></a>  CAccessToken::IsTokenRestricted  
 呼叫此方法以測試是否`CAccessToken`物件包含一份受限制的 Sid。  
  
```
bool IsTokenRestricted() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件包含一份限制 Sid，false，如果沒有任何限制的 Sid，或如果方法失敗，則會傳回 true。  
  
##  <a name="loaduserprofile"></a>  CAccessToken::LoadUserProfile  
 呼叫此方法以載入使用者設定檔相關聯`CAccessToken`物件。  
  
```
bool LoadUserProfile() throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`CAccessToken`不包含有效的語彙基元，或如果使用者設定檔已經存在。  
  
##  <a name="logonuser"></a>  CAccessToken::LogonUser  
 呼叫這個方法來建立與給定認證相關聯之使用者的登入工作階段。  
  
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
 以 null 終止的字串，指定網域或其帳戶資料庫包含的伺服器名稱的指標`pszUserName`帳戶。  
  
 `pszPassword`  
 以 null 終止的字串，指定所指定的使用者帳戶的純文字密碼的指標`pszUserName`。  
  
 *dwLogonType*  
 指定登入要執行作業的類型。 請參閱[LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184)如需詳細資訊。  
  
 *dwLogonProvider*  
 指定登入提供者。 請參閱[LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184)如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 語彙基元所產生的登入相關聯的存取權`CAccessToken`。 若要成功，這個方法`CAccessToken`物件必須保留 SE_TCB_NAME 權限持有者識別為受信任的電腦和基底的一部分。 請參閱[LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184)有關所需的權限。  
  
##  <a name="opencomclienttoken"></a>  CAccessToken::OpenCOMClientToken  
 中呼叫這個方法從 COM 伺服器在處理來自用戶端呼叫以初始化`CAccessToken`COM 用戶端的存取權杖。  
  
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
 如果為 true，目前的執行緒會模擬呼叫的 COM 用戶端，如果這個呼叫成功完成。 如果為 false，將會開啟存取權杖，，但此呼叫完成時，執行緒不會有模擬語彙基元。  
  
 `bOpenAsSelf`  
 指出是否要對執行緒呼叫的安全性內容的存取檢查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法或對呼叫端執行緒的程序的安全性內容。  
  
 如果此參數為 false，使用安全性內容來執行呼叫的執行緒執行存取檢查。 如果執行緒正在模擬用戶端，可以是此安全性內容的用戶端處理序。 此參數為 true，如果使用的安全性內容的程序呼叫的執行緒進行存取檢查。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 [CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖，藉由將建立`bImpersonate`旗標設為*true*。  
  
##  <a name="opennamedpipeclienttoken"></a>  CAccessToken::OpenNamedPipeClientToken  
 中呼叫這個方法從伺服器擷取要求透過具名管道來初始化`CAccessToken`從用戶端的存取權杖。  
  
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
 如果為 true，目前的執行緒會模擬呼叫管道用戶端，如果這個呼叫成功完成。 如果為 false，將會開啟存取權杖，，但此呼叫完成時，執行緒不會有模擬語彙基元。  
  
 `bOpenAsSelf`  
 指出是否要對執行緒呼叫的安全性內容的存取檢查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法或對呼叫端執行緒的程序的安全性內容。  
  
 如果此參數為 false，使用安全性內容來執行呼叫的執行緒執行存取檢查。 如果執行緒正在模擬用戶端，可以是此安全性內容的用戶端處理序。 此參數為 true，如果使用的安全性內容的程序呼叫的執行緒進行存取檢查。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 [CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖，藉由將建立`bImpersonate`旗標設為*true*。  
  
##  <a name="openrpcclienttoken"></a>  CAccessToken::OpenRPCClientToken  
 呼叫這個方法從伺服器處理 RPC 用戶端對初始化的呼叫中`CAccessToken`從用戶端的存取權杖。  
  
```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>參數  
 *BindingHandle*  
 表示用戶端的繫結的伺服器上的繫結控制代碼。  
  
 `dwDesiredAccess`  
 指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。  
  
 `bImpersonate`  
 如果為 true，目前的執行緒會模擬呼叫的 RPC 用戶端，如果這個呼叫成功完成。 如果為 false，將會開啟存取權杖，，但此呼叫完成時，執行緒不會有模擬語彙基元。  
  
 `bOpenAsSelf`  
 指出是否要對執行緒呼叫的安全性內容的存取檢查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法或對呼叫端執行緒的程序的安全性內容。  
  
 如果此參數為 false，使用安全性內容來執行呼叫的執行緒執行存取檢查。 如果執行緒正在模擬用戶端，可以是此安全性內容的用戶端處理序。 此參數為 true，如果使用的安全性內容的程序呼叫的執行緒進行存取檢查。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 [CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖，藉由將建立`bImpersonate`旗標設為*true*。  
  
##  <a name="openthreadtoken"></a>  CAccessToken::OpenThreadToken  
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
 如果為 true，執行緒會保留在要求的模擬層級，此方法完成之後。 如果為 false，執行緒將會還原為其原始的模擬層級。  
  
 `bOpenAsSelf`  
 指出是否要對執行緒呼叫的安全性內容的存取檢查[GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182)方法或對呼叫端執行緒的程序的安全性內容。  
  
 如果此參數為 false，使用安全性內容來執行呼叫的執行緒執行存取檢查。 如果執行緒正在模擬用戶端，可以是此安全性內容的用戶端處理序。 此參數為 true，如果使用的安全性內容的程序呼叫的執行緒進行存取檢查。  
  
 `sil`  
 指定[SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572)列舉的權杖模擬層級提供的型別。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 `OpenThreadToken` 類似於[CAccessToken::GetThreadToken](#getthreadtoken)，但初始化之前設定的模擬等級`CAccessToken`從執行緒的存取權杖。  
  
 [CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖，藉由將建立`bImpersonate`旗標設為*true*。  
  
##  <a name="privilegecheck"></a>  CAccessToken::PrivilegeCheck  
 呼叫此方法以判斷指定的權限集合中已啟用**CAccessToken**物件。  
  
```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
     bool* pbResult) const throw();
```  
  
### <a name="parameters"></a>參數  
 *[Requiredprivileges]*  
 指標[PRIVILEGE_SET](http://msdn.microsoft.com/library/windows/desktop/aa379307)結構。  
  
 *pbResult*  
 值指標的方法會設定指出是否啟用任何或所有指定的權限中`CAccessToken`物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 當`PrivilegeCheck`傳回，**屬性**成員隸屬每個[LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)結構設 SE_PRIVILEGE_USED_FOR_ACCESS，如果已啟用對應的權限。 這個方法會呼叫[PrivilegeCheck](http://msdn.microsoft.com/library/windows/desktop/aa379304) Win32 函式。  
  
##  <a name="revert"></a>  CAccessToken::Revert  
 呼叫這個方法，以停止使用模擬語彙基元的執行緒。  
  
```
bool Revert(HANDLE hThread = NULL) const throw();
```  
  
### <a name="parameters"></a>參數  
 `hThread`  
 若要還原模擬從執行緒的控制代碼。 如果*hThread*是 NULL 時，會假設目前的執行緒。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 可以自動執行模擬語彙基元的回復，與[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)。  
  
##  <a name="setdefaultdacl"></a>  CAccessToken::SetDefaultDacl  
 呼叫此方法以設定預設的 DACL`CAccessToken`物件。  
  
```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rDacl`  
 新的預設值[CDacl 類別](../../atl/reference/cdacl-class.md)資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 預設 DACL 為作用中新的物件建立與這個存取權杖時預設使用的 DACL。  
  
##  <a name="setowner"></a>  CAccessToken::SetOwner  
 呼叫此方法以設定的擁有者`CAccessToken`物件。  
  
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
  
##  <a name="setprimarygroup"></a>  CAccessToken::SetPrimaryGroup  
 呼叫此方法以設定的主要群組`CAccessToken`物件。  
  
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
