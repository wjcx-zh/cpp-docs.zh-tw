---
title: CAccessToken 類別
ms.date: 07/02/2019
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
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
ms.openlocfilehash: d66b126ce5fd6c3da80d2bb4e6322f8180f0b8cf
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552181"
---
# <a name="caccesstoken-class"></a>CAccessToken 類別

這個類別是存取權杖的包裝函式。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

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
|[CAccessToken::Attach](#attach)|呼叫這個方法來取得指定的存取權杖控制代碼的擁有權。|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|呼叫這個方法來判斷指定的 SID 是否已啟用在`CAccessToken`物件。|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|呼叫這個方法來建立新的模擬存取權杖。|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|呼叫這個方法來建立新的主要權杖。|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|呼叫這個方法來建立新的處理程序所表示的使用者安全性內容中執行`CAccessToken`物件。|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|呼叫這個方法來建立新的限制`CAccessToken`物件。|
|[CAccessToken::Detach](#detach)|呼叫這個方法，以撤銷的存取權杖擁有權。|
|[CAccessToken::DisablePrivilege](#disableprivilege)|呼叫這個方法，以停用中的權限`CAccessToken`物件。|
|[CAccessToken::DisablePrivileges](#disableprivileges)|呼叫這個方法，以停用中的一或多個權限`CAccessToken`物件。|
|[CAccessToken::EnablePrivilege](#enableprivilege)|呼叫這個方法來啟用中的權限`CAccessToken`物件。|
|[CAccessToken::EnablePrivileges](#enableprivileges)|呼叫這個方法來啟用中的一或多個權限`CAccessToken`物件。|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|呼叫此方法以傳回`CAccessToken`物件的預設 DACL。|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|呼叫這個方法來取得`CAccessToken`物件等於目前的執行緒在有效的存取權杖。|
|[CAccessToken::GetGroups](#getgroups)|呼叫此方法以傳回`CAccessToken`物件的語彙基元的群組。|
|[CAccessToken::GetHandle](#gethandle)|呼叫這個方法來擷取存取權杖的控制代碼。|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|呼叫這個方法來取得存取權杖中的模擬等級。|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|呼叫這個方法來取得相關聯的登入工作階段識別碼`CAccessToken`物件。|
|[CAccessToken::GetLogonSid](#getlogonsid)|呼叫這個方法來取得相關聯的登入 SID`CAccessToken`物件。|
|[CAccessToken::GetOwner](#getowner)|呼叫這個方法來取得相關聯的擁有者`CAccessToken`物件。|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|呼叫此方法，以取得相關聯的主要群組`CAccessToken`物件。|
|[CAccessToken::GetPrivileges](#getprivileges)|呼叫此方法，以取得相關聯的權限`CAccessToken`物件。|
|[CAccessToken::GetProcessToken](#getprocesstoken)|呼叫這個方法，以所指處理序的存取權杖初始化 `CAccessToken`。|
|[CAccessToken::GetProfile](#getprofile)|呼叫這個方法來取得指向 使用者設定檔相關聯的控制代碼`CAccessToken`物件。|
|[CAccessToken::GetSource](#getsource)|呼叫這個方法來取得來源`CAccessToken`物件。|
|[CAccessToken::GetStatistics](#getstatistics)|呼叫這個方法來取得相關聯的資訊`CAccessToken`物件。|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|呼叫這個方法來取得終端機服務工作階段識別碼相關聯`CAccessToken`物件。|
|[CAccessToken::GetThreadToken](#getthreadtoken)|呼叫這個方法來初始化`CAccessToken`使用從指定的執行緒 token。|
|[CAccessToken::GetTokenId](#gettokenid)|呼叫這個方法來取得權杖識別碼相關聯`CAccessToken`物件。|
|[CAccessToken::GetType](#gettype)|呼叫這個方法來取得的權杖類型`CAccessToken`物件。|
|[CAccessToken::GetUser](#getuser)|呼叫這個方法來識別與相關聯的使用者`CAccessToken`物件。|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|呼叫這個方法來取得指向 使用者設定檔相關聯的控制代碼`CAccessToken`物件。|
|[CAccessToken::Impersonate](#impersonate)|呼叫這個方法來指派模擬`CAccessToken`至執行緒。|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|呼叫此方法以允許模擬登入使用者的安全性內容呼叫的執行緒。|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|呼叫這個方法來測試是否`CAccessToken`物件包含一份受限制的 Sid。|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|呼叫這個方法來載入使用者設定檔相關聯`CAccessToken`物件。|
|[CAccessToken::LogonUser](#logonuser)|呼叫這個方法來建立與指定的認證相關聯使用者的登入工作階段。|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|呼叫這個方法從 COM 伺服器，以處理來自用戶端發出呼叫，以初始化內`CAccessToken`從 COM 用戶端的存取權杖。|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|中呼叫這個方法從伺服器取得要求透過具名管道來初始化`CAccessToken`從用戶端的存取權杖。|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|呼叫這個方法從伺服器處理 RPC 用戶端發出呼叫，以初始化內`CAccessToken`從用戶端的存取權杖。|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|呼叫這個方法來設定模擬等級，然後初始化`CAccessToken`使用從指定的執行緒 token。|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|呼叫這個方法來判斷指定的權限集合中已啟用`CAccessToken`物件。|
|[CAccessToken::Revert](#revert)|呼叫這個方法，以停止執行緒所使用的模擬權杖。|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|呼叫這個方法來設定預設 DACL`CAccessToken`物件。|
|[CAccessToken::SetOwner](#setowner)|呼叫此方法以設定的擁有者`CAccessToken`物件。|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|呼叫此方法以設定的主要群組`CAccessToken`物件。|

## <a name="remarks"></a>備註

[存取權杖](/windows/desktop/SecAuthZ/access-tokens)是說明處理序或執行緒的安全性內容，並配置給每位使用者登入 Windows 系統的物件。

在 Windows 中的存取控制模型的簡介，請參閱 <<c0> [ 存取控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="requirements"></a>需求

**標頭：** atlsecurity.h

##  <a name="attach"></a>  CAccessToken::Attach

呼叫這個方法來取得指定的存取權杖控制代碼的擁有權。

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>參數

*hToken*<br/>
存取權杖控制代碼。

### <a name="remarks"></a>備註

在偵錯組建中，判斷提示就會發生錯誤，如果`CAccessToken`物件已有的存取權杖擁有權。

##  <a name="dtor"></a>  CAccessToken::~CAccessToken

解構函式。

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="checktokenmembership"></a>  CAccessToken::CheckTokenMembership

呼叫這個方法來判斷指定的 SID 是否已啟用在`CAccessToken`物件。

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
若要參考[CSid 類別](../../atl/reference/csid-class.md)物件。

*pbIsMember*<br/>
指標，此變數會接收檢查的結果。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

`CheckTokenMembership`方法會檢查是否存在的 sid，在使用者和群組 Sid 的存取權杖。 如果 SID，且具有 SE_GROUP_ENABLED 屬性*pbIsMember*是設定為 TRUE，否則它會設定為 FALSE。

在偵錯組建中，判斷提示就會發生錯誤，如果*pbIsMember*不是有效的指標。

> [!NOTE]
>  `CAccessToken`物件必須是模擬權杖，且不是主要的權杖。

##  <a name="createimpersonationtoken"></a>  CAccessToken::CreateImpersonationToken

呼叫這個方法來建立模擬的存取權杖。

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>參數

*pImp*<br/>
新的指標`CAccessToken`物件。

*sil*<br/>
指定[SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level)列舉型別，提供新的權杖模擬等級。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

`CreateImpersonationToken` 呼叫[DuplicateToken](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-duplicatetoken)來建立新的模擬語彙基元。

##  <a name="createprimarytoken"></a>  CAccessToken::CreatePrimaryToken

呼叫這個方法來建立新的主要權杖。

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pPri*<br/>
新的指標`CAccessToken`物件。

*dwDesiredAccess*<br/>
指定新的權杖要求的存取權限。 預設值，MAXIMUM_ALLOWED，要求所有呼叫端的有效存取權限。 請參閱[存取權限和存取遮罩](/windows/desktop/SecAuthZ/access-rights-and-access-masks)的更多的存取權限。

*pTokenAttributes*<br/>
指標[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構，指定新的權杖的安全性描述元，並判斷子處理序是否可以繼承的語彙基元。 如果*pTokenAttributes*是 NULL，此語彙基元取得預設安全性描述元，而且無法繼承控制代碼。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

`CreatePrimaryToken` 呼叫[DuplicateTokenEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex)來建立新的主要權杖。

##  <a name="createprocessasuser"></a>  CAccessToken::CreateProcessAsUser

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

*pApplicationName*<br/>
以 null 終止的字串，指定要執行之模組的指標。 此參數不可以是 NULL。

*pCommandLine*<br/>
以 null 終止的字串，指定要執行的命令列的指標。

*pProcessInformation*<br/>
指標[PROCESS_INFORMATION 結構](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information)接收新的處理序的識別資訊。

*pStartupInfo*<br/>
指標[STARTUPINFO](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_startupinfoa)結構，指定新的處理序的主視窗的顯示方式。

*dwCreationFlags*<br/>
指定控制項的優先權類別] 和 [建立處理程序的其他旗標。 請參閱 Win32 函式[CreateProcessAsUser](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessasusera)旗標的清單。

*bLoadProfile*<br/>
如果為 TRUE，會載入使用者設定檔[LoadUserProfile](/windows/desktop/api/userenv/nf-userenv-loaduserprofilea)。

*pProcessAttributes*<br/>
指標[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構，指定新的處理序的安全性描述元，並判斷子處理序是否可以繼承傳回的控制代碼。 如果*pProcessAttributes*是 NULL，此程序取得的預設安全性描述元，而且無法繼承控制代碼。

*pThreadAttributes*<br/>
指標[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構，指定新的執行緒的安全性描述元，並判斷子處理序是否可以繼承傳回的控制代碼。 如果*pThreadAttributes*是 NULL，執行緒會取得預設安全性描述元，而且無法繼承控制代碼。

*bInherit*<br/>
指出是否在新處理序會繼承控制代碼呼叫處理序。 如果為 TRUE，新的處理序會繼承呼叫處理序中每個可繼承的開啟控制代碼。 繼承的控制代碼具有相同的值與存取權限，原始的控制代碼的形式。

*pCurrentDirectory*<br/>
以 null 終止的字串，指定目前的磁碟機和目錄的新處理序的指標。 字串必須包含磁碟機代號的完整路徑。 如果此參數為 NULL，新處理序會為呼叫處理序有相同的目前磁碟機和目錄。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

`CreateProcessAsUser` 會使用`CreateProcessAsUser`Win32 函式來建立新的處理序中所表示的使用者的安全性內容執行`CAccessToken`物件。 請參閱 popis [CreateProcessAsUser](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessasusera)函式所需的參數的完整討論。

若要成功，這個方法`CAccessToken`（除非它是限制的權杖），物件必須保留 AssignPrimaryToken 和 IncreaseQuota 權限。

##  <a name="createrestrictedtoken"></a>  CAccessToken::CreateRestrictedToken

呼叫這個方法來建立新的限制`CAccessToken`物件。

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>參數

*pRestrictedToken*<br/>
新的限制`CAccessToken`物件。

*SidsToDisable*<br/>
A`CTokenGroups`物件，指定禁用 Sid。

*SidsToRestrict*<br/>
A`CTokenGroups`物件，指定限制的 Sid。

*PrivilegesToDelete*<br/>
A`CTokenPrivileges`物件，指定要刪除權限限制的權杖中。 預設會建立空的物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

`CreateRestrictedToken` 會使用[CreateRestrictedToken](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken)來建立新的 Win32 函式`CAccessToken`物件，但有限制。

> [!IMPORTANT]
>  使用時`CreateRestrictedToken`，請確認下列事項： 現有的語彙基元且有效 （未由使用者輸入） 和*SidsToDisable*並*PrivilegesToDelete*都有效 （且無法由使用者輸入）。 如果方法傳回 FALSE，則拒絕功能。

##  <a name="detach"></a>  CAccessToken::Detach

呼叫這個方法，以撤銷的存取權杖擁有權。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>傳回值

傳回的控制代碼`CAccessToken`的已卸離。

### <a name="remarks"></a>備註

這個方法會撤銷`CAccessToken`的擁有權的存取權杖。

##  <a name="disableprivilege"></a>  CAccessToken::DisablePrivilege

呼叫這個方法，以停用中的權限`CAccessToken`物件。

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*pszPrivilege*<br/>
字串，包含在中停用的權限的指標`CAccessToken`物件。

*pPreviousState*<br/>
指標`CTokenPrivileges`其中將包含先前的權限狀態的物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="disableprivileges"></a>  CAccessToken::DisablePrivileges

呼叫這個方法，以停用中的一或多個權限`CAccessToken`物件。

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*rPrivileges*<br/>
包含要在停用的權限的字串陣列的指標`CAccessToken`物件。

*pPreviousState*<br/>
指標`CTokenPrivileges`其中將包含先前的權限狀態的物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="enableprivilege"></a>  CAccessToken::EnablePrivilege

呼叫這個方法來啟用中的權限`CAccessToken`物件。

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*pszPrivilege*<br/>
字串，包含要在中啟用的權限的指標`CAccessToken`物件。

*pPreviousState*<br/>
指標`CTokenPrivileges`其中將包含先前的權限狀態的物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="enableprivileges"></a>  CAccessToken::EnablePrivileges

呼叫這個方法來啟用中的一或多個權限`CAccessToken`物件。

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*rPrivileges*<br/>
包含要在中啟用的權限的字串陣列的指標`CAccessToken`物件。

*pPreviousState*<br/>
指標`CTokenPrivileges`其中將包含先前的權限狀態的物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="getdefaultdacl"></a>  CAccessToken::GetDefaultDacl

呼叫此方法以傳回`CAccessToken`物件的預設 DACL。

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>參數

*pDacl*<br/>
指標[CDacl 類別](../../atl/reference/cdacl-class.md)物件將會收到`CAccessToken`物件的預設 DACL。

### <a name="return-value"></a>傳回值

如果預設 DACL 已復原，則為 FALSE 否則為 true，則傳回。

##  <a name="geteffectivetoken"></a>  CAccessToken::GetEffectiveToken

呼叫這個方法來取得`CAccessToken`物件等於目前的執行緒在有效的存取權杖。

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>參數

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="getgroups"></a>  CAccessToken::GetGroups

呼叫此方法以傳回`CAccessToken`物件的語彙基元的群組。

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>參數

*pGroups*<br/>
指標[CTokenGroups 類別](../../atl/reference/ctokengroups-class.md)可接收群組資訊的物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="gethandle"></a>  CAccessToken::GetHandle

呼叫這個方法來擷取存取權杖的控制代碼。

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>傳回值

傳回的控制代碼`CAccessToken`物件的存取權杖。

##  <a name="getimpersonationlevel"></a>  CAccessToken::GetImpersonationLevel

呼叫這個方法來取得存取權杖中的模擬等級。

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>參數

*pImpersonationLevel*<br/>
指標[SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level)列舉型別可接收模擬層級資訊。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="getlogonsessionid"></a>  CAccessToken::GetLogonSessionId

呼叫這個方法來取得相關聯的登入工作階段識別碼`CAccessToken`物件。

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>參數

*pluid*<br/>
指標[LUID](/windows/desktop/api/winnt/ns-winnt-_luid)這將會收到登入工作階段識別碼。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

在偵錯組建中，判斷提示就會發生錯誤，如果*pluid*是無效的值。

##  <a name="getlogonsid"></a>  CAccessToken::GetLogonSid

呼叫這個方法來取得相關聯的登入 SID`CAccessToken`物件。

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指標[CSid 類別](../../atl/reference/csid-class.md)物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

在偵錯組建中，判斷提示就會發生錯誤，如果*pSid*是無效的值。

##  <a name="getowner"></a>  CAccessToken::GetOwner

呼叫這個方法來取得相關聯的擁有者`CAccessToken`物件。

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指標[CSid 類別](../../atl/reference/csid-class.md)物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

擁有者是由建立此存取權杖生效時的所有物件上的預設設定。

##  <a name="getprimarygroup"></a>  CAccessToken::GetPrimaryGroup

呼叫此方法，以取得相關聯的主要群組`CAccessToken`物件。

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指標[CSid 類別](../../atl/reference/csid-class.md)物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

在此存取權杖生效時所建立的所有物件上的預設設定群組。

##  <a name="getprivileges"></a>  CAccessToken::GetPrivileges

呼叫此方法，以取得相關聯的權限`CAccessToken`物件。

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>參數

*pPrivileges*<br/>
指標[CTokenPrivileges 類別](../../atl/reference/ctokenprivileges-class.md)可接收的權限的物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="getprocesstoken"></a>  CAccessToken::GetProcessToken

呼叫這個方法，以所指處理序的存取權杖初始化 `CAccessToken`。

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>參數

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*hProcess*<br/>
處理已開啟存取權杖的處理序。 如果使用預設值是 NULL，則會使用目前的處理序。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

呼叫[OpenProcessToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32 函式。

##  <a name="getprofile"></a>  CAccessToken::GetProfile

呼叫這個方法來取得指向 使用者設定檔相關聯的控制代碼`CAccessToken`物件。

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>傳回值

傳回的控制代碼，如果不有任何設定檔，指向使用者設定檔或 NULL。

##  <a name="getsource"></a>  CAccessToken::GetSource

呼叫這個方法來取得來源`CAccessToken`物件。

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>參數

*pSource*<br/>
指標[TOKEN_SOURCE](/windows/desktop/api/winnt/ns-winnt-_token_source)結構。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="getstatistics"></a>  CAccessToken::GetStatistics

呼叫這個方法來取得相關聯的資訊`CAccessToken`物件。

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>參數

*pStatistics*<br/>
指標[TOKEN_STATISTICS](/windows/desktop/api/winnt/ns-winnt-_token_statistics)結構。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="getterminalservicessessionid"></a>  CAccessToken::GetTerminalServicesSessionId

呼叫這個方法來取得終端機服務工作階段識別碼相關聯`CAccessToken`物件。

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>參數

*pdwSessionId*<br/>
終端機服務工作階段識別碼。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="getthreadtoken"></a>  CAccessToken::GetThreadToken

呼叫這個方法來初始化`CAccessToken`使用從指定的執行緒 token。

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>參數

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*hThread*<br/>
執行緒已開啟的存取權杖的控制代碼。

*bOpenAsSelf*<br/>
存取檢查是否對執行緒呼叫的安全性內容提出`GetThreadToken`方法或呼叫端執行緒的程序的安全性內容。

如果此參數為 FALSE 時，會執行存取檢查，呼叫執行緒中使用的安全性內容。 如果執行緒模擬用戶端，此安全性內容可以是用戶端處理序。 如果此參數為 TRUE，存取檢查會使用呼叫執行緒的處理程序的安全性內容。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="gettokenid"></a>  CAccessToken::GetTokenId

呼叫這個方法來取得權杖識別碼相關聯`CAccessToken`物件。

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>參數

*pluid*<br/>
指標[LUID](/windows/desktop/api/winnt/ns-winnt-_luid)這將會收到權杖的識別碼。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="gettype"></a>  CAccessToken::GetType

呼叫這個方法來取得的權杖類型`CAccessToken`物件。

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>參數

*pType*<br/>
位址[TOKEN_TYPE](/windows/desktop/api/winnt/ne-winnt-_token_type) ，成功時，收到的權杖類型的變數。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

TOKEN_TYPE 列舉型別包含區分主要權杖與模擬語彙基元的值。

##  <a name="getuser"></a>  CAccessToken::GetUser

呼叫這個方法來識別與相關聯的使用者`CAccessToken`物件。

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指標[CSid 類別](../../atl/reference/csid-class.md)物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

##  <a name="hkeycurrentuser"></a>  CAccessToken::HKeyCurrentUser

呼叫這個方法來取得指向 使用者設定檔相關聯的控制代碼`CAccessToken`物件。

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>傳回值

傳回的控制代碼，如果不有任何設定檔，指向使用者設定檔或 NULL。

##  <a name="impersonate"></a>  CAccessToken::Impersonate

呼叫這個方法來指派模擬`CAccessToken`至執行緒。

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*hThread*<br/>
要指派的模擬權杖執行緒的控制代碼。 這個控制代碼必須已經開啟 TOKEN_IMPERSONATE 存取權限。 如果*hThread*是 NULL，方法會導致執行緒停止使用模擬 token。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

在偵錯組建中，判斷提示就會發生錯誤，如果`CAccessToken`沒有權杖的有效指標。

[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原模擬的存取權杖。

##  <a name="impersonateloggedonuser"></a>  CAccessToken::ImpersonateLoggedOnUser

呼叫此方法以允許模擬登入使用者的安全性內容呼叫的執行緒。

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

> [!IMPORTANT]
>  如果模擬函式的呼叫失敗，因為任何原因，無法模擬該用戶端和用戶端要求中進行呼叫的程序的安全性內容。 如果處理序正在執行做為高特殊權限的帳戶，或身為系統管理群組成員，使用者可能無法執行動作他或她否則不允許。 因此，應該一律確認此函式的傳回值。

##  <a name="istokenrestricted"></a>  CAccessToken::IsTokenRestricted

呼叫這個方法來測試是否`CAccessToken`物件包含一份受限制的 Sid。

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>傳回值

如果物件包含一份限制 Sid，則為 FALSE，如果不有任何限制的 Sid，或如果方法失敗，則傳回 TRUE。

##  <a name="loaduserprofile"></a>  CAccessToken::LoadUserProfile

呼叫這個方法來載入使用者設定檔相關聯`CAccessToken`物件。

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

在偵錯組建中，判斷提示就會發生錯誤，如果`CAccessToken`不包含有效的語彙基元，或如果使用者設定檔已經存在。

##  <a name="logonuser"></a>  CAccessToken::LogonUser

呼叫這個方法來建立與指定的認證相關聯使用者的登入工作階段。

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>參數

*pszUserName*<br/>
以 null 終止的字串，指定使用者名稱的指標。 這是登入的使用者帳戶的名稱。

*pszDomain*<br/>
以 null 終止的字串，指定的網域或其帳戶的資料庫包含的伺服器名稱的指標*pszUserName*帳戶。

*pszPassword*<br/>
以 null 終止的字串，指定所指定的使用者帳戶的純文字密碼的指標*pszUserName*。

*dwLogonType*<br/>
指定登入要執行作業的類型。 請參閱[LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera)如需詳細資訊。

*dwLogonProvider*<br/>
指定登入提供者。 請參閱[LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera)如需詳細資訊。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

語彙基元所產生的登入相關聯的存取權`CAccessToken`。 若要成功，這個方法`CAccessToken`物件必須保留有 SE_TCB_NAME 權限，識別持有者為受信任的電腦和基底的一部分。 請參閱[LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera)如有關所需的權限的詳細資訊。

##  <a name="opencomclienttoken"></a>  CAccessToken::OpenCOMClientToken

呼叫這個方法從 COM 伺服器，以處理來自用戶端發出呼叫，以初始化內`CAccessToken`從 COM 用戶端的存取權杖。

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>參數

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*bImpersonate*<br/>
如果為 TRUE，目前的執行緒會模擬呼叫的 COM 用戶端，即使已成功完成這個呼叫。 如果為 FALSE，存取權杖也會開啟，但當此呼叫完成時，執行緒不會有模擬語彙基元。

*bOpenAsSelf*<br/>
存取檢查是否對執行緒呼叫的安全性內容提出[GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法或呼叫端執行緒的程序的安全性內容。

如果此參數為 FALSE 時，會執行存取檢查，呼叫執行緒中使用的安全性內容。 如果執行緒模擬用戶端，此安全性內容可以是用戶端處理序。 如果此參數為 TRUE，存取檢查會使用呼叫執行緒的處理程序的安全性內容。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原所設定的模擬的存取權杖*bImpersonate*旗標設為 TRUE。

##  <a name="opennamedpipeclienttoken"></a>  CAccessToken::OpenNamedPipeClientToken

中呼叫這個方法從伺服器取得要求透過具名管道來初始化`CAccessToken`從用戶端的存取權杖。

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>參數

*hPipe*<br/>
具名管道的控制代碼。

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*bImpersonate*<br/>
如果為 TRUE，目前的執行緒會模擬呼叫管道用戶端，即使已成功完成這個呼叫。 如果為 FALSE，存取權杖也會開啟，但當此呼叫完成時，執行緒不會有模擬語彙基元。

*bOpenAsSelf*<br/>
存取檢查是否對執行緒呼叫的安全性內容提出[GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法或呼叫端執行緒的程序的安全性內容。

如果此參數為 FALSE 時，會執行存取檢查，呼叫執行緒中使用的安全性內容。 如果執行緒模擬用戶端，此安全性內容可以是用戶端處理序。 如果此參數為 TRUE，存取檢查會使用呼叫執行緒的處理程序的安全性內容。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原所設定的模擬的存取權杖*bImpersonate*旗標設為 TRUE。

##  <a name="openrpcclienttoken"></a>  CAccessToken::OpenRPCClientToken

呼叫這個方法從伺服器處理 RPC 用戶端發出呼叫，以初始化內`CAccessToken`從用戶端的存取權杖。

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>參數

*BindingHandle*<br/>
表示用戶端的繫結的伺服器上的繫結控制代碼。

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*bImpersonate*<br/>
如果為 TRUE，目前的執行緒會模擬呼叫的 RPC 用戶端，即使已成功完成這個呼叫。 如果為 FALSE，存取權杖也會開啟，但當此呼叫完成時，執行緒不會有模擬語彙基元。

*bOpenAsSelf*<br/>
存取檢查是否對執行緒呼叫的安全性內容提出[GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法或呼叫端執行緒的程序的安全性內容。

如果此參數為 FALSE 時，會執行存取檢查，呼叫執行緒中使用的安全性內容。 如果執行緒模擬用戶端，此安全性內容可以是用戶端處理序。 如果此參數為 TRUE，存取檢查會使用呼叫執行緒的處理程序的安全性內容。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原所設定的模擬的存取權杖*bImpersonate*旗標設為 TRUE。

##  <a name="openthreadtoken"></a>  CAccessToken::OpenThreadToken

呼叫這個方法來設定模擬等級，然後初始化`CAccessToken`使用從指定的執行緒 token。

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>參數

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*bImpersonate*<br/>
如果為 TRUE，執行緒會保留在要求的模擬層級，這個方法完成之後。 如果為 FALSE，執行緒將會還原為其原始的模擬層級。

*bOpenAsSelf*<br/>
存取檢查是否對執行緒呼叫的安全性內容提出[GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法或呼叫端執行緒的程序的安全性內容。

如果此參數為 FALSE 時，會執行存取檢查，呼叫執行緒中使用的安全性內容。 如果執行緒模擬用戶端，此安全性內容可以是用戶端處理序。 如果此參數為 TRUE，存取檢查會使用呼叫執行緒的處理程序的安全性內容。

*sil*<br/>
指定[SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level)列舉型別，提供語彙基元的模擬層級。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

`OpenThreadToken` 類似於[CAccessToken::GetThreadToken](#getthreadtoken)，但設定的模擬等級，然後再初始化`CAccessToken`從執行緒的存取權杖。

[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用來自動還原所設定的模擬的存取權杖*bImpersonate*旗標設為 TRUE。

##  <a name="privilegecheck"></a>  CAccessToken::PrivilegeCheck

呼叫這個方法來判斷指定的權限集合中已啟用`CAccessToken`物件。

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>參數

*RequiredPrivileges*<br/>
指標[PRIVILEGE_SET](/windows/desktop/api/winnt/ns-winnt-_privilege_set)結構。

*pbResult*<br/>
指出是否啟用任何或所有指定的權限中的值指標方法設定`CAccessToken`物件。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

當`PrivilegeCheck`會傳回`Attributes`每個成員[LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes)結構設 SE_PRIVILEGE_USED_FOR_ACCESS，如果已啟用對應的權限。 這個方法會呼叫[PrivilegeCheck](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32 函式。

##  <a name="revert"></a>  CAccessToken::Revert

呼叫這個方法，以停止從使用模擬語彙基元的執行緒。

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>參數

*hThread*<br/>
若要還原的模擬執行緒的控制代碼。 如果*hThread*是 NULL，會假設目前的執行緒。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

可以自動執行的模擬語彙基元回復，與[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)。

##  <a name="setdefaultdacl"></a>  CAccessToken::SetDefaultDacl

呼叫這個方法來設定預設 DACL`CAccessToken`物件。

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>參數

*rDacl*<br/>
新的預設值[CDacl 類別](../../atl/reference/cdacl-class.md)資訊。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

預設 DACL 為作用中的新物件建立與此存取權杖時，會將預設使用的 DACL。

##  <a name="setowner"></a>  CAccessToken::SetOwner

呼叫此方法以設定的擁有者`CAccessToken`物件。

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
[CSid 類別](../../atl/reference/csid-class.md)物件，其中包含擁有者資訊。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

擁有者是用於建立此存取權杖生效時的新物件的預設擁有者。

##  <a name="setprimarygroup"></a>  CAccessToken::SetPrimaryGroup

呼叫此方法以設定的主要群組`CAccessToken`物件。

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
[CSid 類別](../../atl/reference/csid-class.md)物件，包含主要群組資訊。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

主要群組是建立此存取權杖生效時的新物件的預設群組。

## <a name="see-also"></a>另請參閱

[ATLSecurity 範例](../../overview/visual-cpp-samples.md)<br/>
[存取權杖](/windows/desktop/SecAuthZ/access-tokens)<br/>
[類別概觀](../../atl/atl-class-overview.md)
