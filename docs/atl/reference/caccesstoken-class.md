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
ms.openlocfilehash: 33fbaae5dafaccdf7f7e6880eaa42dd68352e840
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418157"
---
# <a name="caccesstoken-class"></a>CAccessToken 類別

此類別是存取權杖的包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAccessToken
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAccessToken：： ~ CAccessToken](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAccessToken：： Attach](#attach)|呼叫此方法以取得給定存取權杖控制碼的擁有權。|
|[CAccessToken：： CheckTokenMembership](#checktokenmembership)|呼叫這個方法，以判斷 `CAccessToken` 物件中是否已啟用指定的 SID。|
|[CAccessToken：： CreateImpersonationToken](#createimpersonationtoken)|呼叫這個方法，以建立新的模擬存取權杖。|
|[CAccessToken：： CreatePrimaryToken](#createprimarytoken)|呼叫這個方法，以建立新的主要權杖。|
|[CAccessToken：： CreateProcessAsUser](#createprocessasuser)|呼叫這個方法，在 `CAccessToken` 物件所表示之使用者的安全性內容中，建立執行的新進程。|
|[CAccessToken：： CreateRestrictedToken](#createrestrictedtoken)|呼叫這個方法，以建立新的受限制 `CAccessToken` 物件。|
|[CAccessToken：:D etach](#detach)|呼叫此方法以撤銷存取權杖的擁有權。|
|[CAccessToken：:D isablePrivilege](#disableprivilege)|呼叫這個方法，以停用 `CAccessToken` 物件中的許可權。|
|[CAccessToken：:D isablePrivileges](#disableprivileges)|呼叫這個方法，以停用 `CAccessToken` 物件中的一或多個許可權。|
|[CAccessToken：： EnablePrivilege](#enableprivilege)|呼叫這個方法，以在 `CAccessToken` 物件中啟用許可權。|
|[CAccessToken：： EnablePrivileges](#enableprivileges)|呼叫這個方法，以啟用 `CAccessToken` 物件中的一或多個許可權。|
|[CAccessToken：： GetDefaultDacl](#getdefaultdacl)|呼叫這個方法，以傳回 `CAccessToken` 物件的預設 DACL。|
|[CAccessToken：： GetEffectiveToken](#geteffectivetoken)|呼叫這個方法，讓 `CAccessToken` 物件等於目前線程的作用中存取權杖。|
|[CAccessToken：： GetGroups](#getgroups)|呼叫這個方法，以傳回 `CAccessToken` 物件的 token 群組。|
|[CAccessToken：： GetHandle](#gethandle)|呼叫這個方法來抓取存取權杖的控制碼。|
|[CAccessToken：： GetImpersonationLevel](#getimpersonationlevel)|呼叫這個方法，從存取權杖取得模擬層級。|
|[CAccessToken：： GetLogonSessionId](#getlogonsessionid)|呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的登入會話識別碼。|
|[CAccessToken：： GetLogonSid](#getlogonsid)|呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的登入 SID。|
|[CAccessToken：： GetOwner](#getowner)|呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的擁有者。|
|[CAccessToken：： GetPrimaryGroup](#getprimarygroup)|呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的主要群組。|
|[CAccessToken：： GetPrivileges](#getprivileges)|呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的許可權。|
|[CAccessToken：： GetProcessToken](#getprocesstoken)|呼叫這個方法，以所指處理序的存取權杖初始化 `CAccessToken`。|
|[CAccessToken：： GetProfile](#getprofile)|呼叫這個方法，以取得指向與 `CAccessToken` 物件相關聯之使用者設定檔的控制碼。|
|[CAccessToken：： GetSource](#getsource)|呼叫這個方法以取得 `CAccessToken` 物件的來源。|
|[CAccessToken：： GetStatistics](#getstatistics)|呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的資訊。|
|[CAccessToken：： GetTerminalServicesSessionId](#getterminalservicessessionid)|呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的終端機服務會話識別碼。|
|[CAccessToken：： GetThreadToken](#getthreadtoken)|呼叫這個方法，以使用來自給定執行緒的 token 來初始化 `CAccessToken`。|
|[CAccessToken：： GetTokenId](#gettokenid)|呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的 Token 識別碼。|
|[CAccessToken：： GetType](#gettype)|呼叫這個方法，以取得 `CAccessToken` 物件的 token 類型。|
|[CAccessToken：： GetUser](#getuser)|呼叫這個方法，以識別與 `CAccessToken` 物件相關聯的使用者。|
|[CAccessToken：： HKeyCurrentUser](#hkeycurrentuser)|呼叫這個方法，以取得指向與 `CAccessToken` 物件相關聯之使用者設定檔的控制碼。|
|[CAccessToken：：模擬](#impersonate)|呼叫這個方法，將模擬 `CAccessToken` 指派給執行緒。|
|[CAccessToken：： ImpersonateLoggedOnUser](#impersonateloggedonuser)|呼叫此方法可讓呼叫執行緒模擬已登入使用者的安全性內容。|
|[CAccessToken：： IsTokenRestricted](#istokenrestricted)|呼叫這個方法來測試 `CAccessToken` 物件是否包含受限制的 Sid 清單。|
|[CAccessToken：： LoadUserProfile](#loaduserprofile)|呼叫這個方法，載入與 `CAccessToken` 物件相關聯的使用者設定檔。|
|[CAccessToken：： LogonUser](#logonuser)|呼叫這個方法，為與指定認證相關聯的使用者建立登入會話。|
|[CAccessToken：： OpenCOMClientToken](#opencomclienttoken)|從 COM 伺服器內呼叫此方法，以處理來自用戶端的呼叫，以使用來自 COM 用戶端的存取權杖來初始化 `CAccessToken`。|
|[CAccessToken：： OpenNamedPipeClientToken](#opennamedpipeclienttoken)|從伺服器內呼叫此方法，透過具名管道取得要求，使用來自用戶端的存取權杖初始化 `CAccessToken`。|
|[CAccessToken：： OpenRPCClientToken](#openrpcclienttoken)|從處理 RPC 用戶端呼叫的伺服器內呼叫此方法，以使用來自用戶端的存取權杖來初始化 `CAccessToken`。|
|[CAccessToken：： OpenThreadToken](#openthreadtoken)|呼叫這個方法以設定模擬層級，然後使用來自給定執行緒的權杖初始化 `CAccessToken`。|
|[CAccessToken：:P rivilegeCheck](#privilegecheck)|呼叫這個方法，以判斷是否在 `CAccessToken` 物件中啟用一組指定的許可權。|
|[CAccessToken：： Revert](#revert)|呼叫這個方法，以停止使用模擬 token 的執行緒。|
|[CAccessToken：： SetDefaultDacl](#setdefaultdacl)|呼叫這個方法，以設定 `CAccessToken` 物件的預設 DACL。|
|[CAccessToken：： SetOwner](#setowner)|呼叫這個方法來設定 `CAccessToken` 物件的擁有者。|
|[CAccessToken：： SetPrimaryGroup](#setprimarygroup)|呼叫這個方法，以設定 `CAccessToken` 物件的主要群組。|

## <a name="remarks"></a>備註

[存取權杖](/windows/win32/SecAuthZ/access-tokens)是一種物件，可描述處理常式或執行緒的安全性內容，並配置給每位登入 Windows 系統的使用者。

如需 Windows 中的存取控制模型簡介，請參閱 Windows SDK 中的[存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標頭：** atlsecurity。h

##  <a name="attach"></a>CAccessToken：： Attach

呼叫此方法以取得給定存取權杖控制碼的擁有權。

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>參數

*hToken*<br/>
存取權杖的控制碼。

### <a name="remarks"></a>備註

在 [偵錯工具] 組建中，如果 `CAccessToken` 物件已經有存取權杖的擁有權，就會發生判斷提示錯誤。

##  <a name="dtor"></a>CAccessToken：： ~ CAccessToken

解構函式。

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="checktokenmembership"></a>CAccessToken：： CheckTokenMembership

呼叫這個方法，以判斷 `CAccessToken` 物件中是否已啟用指定的 SID。

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
[CSid 類別](../../atl/reference/csid-class.md)物件的參考。

*pbIsMember*<br/>
接收檢查結果之變數的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

`CheckTokenMembership` 方法會檢查使用者的 SID 是否存在，以及存取權杖的群組 Sid。 如果 SID 存在，而且具有 SE_GROUP_ENABLED 屬性， *pbIsMember*會設定為 TRUE;否則，它會設定為 FALSE。

在 [偵錯工具] 組建中，如果*pbIsMember*不是有效的指標，就會發生判斷提示錯誤。

> [!NOTE]
>  `CAccessToken` 物件必須是模擬 token，而不是主要 token。

##  <a name="createimpersonationtoken"></a>CAccessToken：： CreateImpersonationToken

呼叫這個方法來建立模擬存取權杖。

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>參數

*pImp*<br/>
新 `CAccessToken` 物件的指標。

*sil*<br/>
指定提供新權杖之模擬層級的[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)列舉類型。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

`CreateImpersonationToken` 會呼叫[DuplicateToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken)來建立新的模擬權杖。

##  <a name="createprimarytoken"></a>CAccessToken：： CreatePrimaryToken

呼叫這個方法，以建立新的主要權杖。

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pPri*<br/>
新 `CAccessToken` 物件的指標。

*dwDesiredAccess*<br/>
指定新權杖的要求存取權限。 預設的 MAXIMUM_ALLOWED 會要求對呼叫者有效的所有存取權限。 如需存取權限的詳細資訊，請參閱[存取權限和存取遮罩](/windows/win32/SecAuthZ/access-rights-and-access-masks)。

*pTokenAttributes*<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構的指標，指定新權杖的安全描述項，並決定子進程是否可以繼承該 token。 如果*pTokenAttributes*為 Null，則權杖會取得預設的安全描述項，而且無法繼承控制碼。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

`CreatePrimaryToken` 會呼叫[DuplicateTokenEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex)來建立新的主要權杖。

##  <a name="createprocessasuser"></a>CAccessToken：： CreateProcessAsUser

呼叫這個方法，在 `CAccessToken` 物件所表示之使用者的安全性內容中，建立執行的新進程。

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
以 null 結束的字串指標，指定要執行的模組。 這個參數不可以是 Null。

*pCommandLine*<br/>
以 null 結束的字串指標，指定要執行的命令列。

*pProcessInformation*<br/>
接收新進程之識別資訊的[PROCESS_INFORMATION 結構](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information)的指標。

*pStartupInfo*<br/>
[STARTUPINFO](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow)結構的指標，指定新處理常式的主視窗應該如何出現。

*dwCreationFlags*<br/>
指定其他旗標，以控制優先順序類別和進程的建立。 如需旗標的清單，請參閱 Win32 函數[CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) 。

*bLoadProfile*<br/>
若為 TRUE，則會使用[LoadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew)載入使用者的設定檔。

*pProcessAttributes*<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構的指標，指定新進程的安全描述項，並決定子進程是否可以繼承傳回的控制碼。 如果*pProcessAttributes*為 Null，進程會取得預設的安全描述項，而且無法繼承控制碼。

*pThreadAttributes*<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構的指標，指定新執行緒的安全描述項，並決定子進程是否可以繼承傳回的控制碼。 如果*pThreadAttributes*為 Null，則執行緒會取得預設的安全描述項，而且無法繼承控制碼。

*bInherit*<br/>
指出新的進程是否繼承呼叫進程的控制碼。 若為 TRUE，新的進程會繼承呼叫進程中每個可繼承的開啟控制碼。 繼承的控制碼與原始控制碼具有相同的值和存取權限。

*pCurrentDirectory*<br/>
以 null 結束的字串指標，指定新進程的目前磁片磁碟機和目錄。 此字串必須是包含磁碟機號的完整路徑。 如果此參數為 Null，新的進程將會具有與呼叫進程相同的目前磁片磁碟機和目錄。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

`CreateProcessAsUser` 會使用 `CreateProcessAsUser` Win32 函式來建立新的處理常式，該進程會在 `CAccessToken` 物件所代表之使用者的安全性內容中執行。 請參閱[CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw)函數的說明，以取得所需參數的完整討論。

若要讓此方法成功，`CAccessToken` 物件必須保留 AssignPrimaryToken （除非它是受限制的 token）和 IncreaseQuota 許可權。

##  <a name="createrestrictedtoken"></a>CAccessToken：： CreateRestrictedToken

呼叫這個方法，以建立新的受限制 `CAccessToken` 物件。

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>參數

*pRestrictedToken*<br/>
新的、受限制的 `CAccessToken` 物件。

*SidsToDisable*<br/>
指定僅拒絕 Sid 的 `CTokenGroups` 物件。

*SidsToRestrict*<br/>
指定限制 Sid 的 `CTokenGroups` 物件。

*PrivilegesToDelete*<br/>
`CTokenPrivileges` 物件，指定要在限制的權杖中刪除的許可權。 預設會建立空的物件。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

`CreateRestrictedToken` 使用[CreateRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) Win32 函式來建立新的 `CAccessToken` 物件，並具有限制。

> [!IMPORTANT]
>  使用 `CreateRestrictedToken`時，請確定下列事項：現有的權杖有效（而且不是由使用者輸入），而且*SidsToDisable*和*PrivilegesToDelete*都是有效的（而且不是由使用者輸入）。 如果方法傳回 FALSE，則拒絕功能。

##  <a name="detach"></a>CAccessToken：:D etach

呼叫此方法以撤銷存取權杖的擁有權。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>傳回值

傳回已卸離之 `CAccessToken` 的控制碼。

### <a name="remarks"></a>備註

這個方法會撤銷 `CAccessToken`的存取權杖擁有權。

##  <a name="disableprivilege"></a>CAccessToken：:D isablePrivilege

呼叫這個方法，以停用 `CAccessToken` 物件中的許可權。

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*pszPrivilege*<br/>
字串的指標，其中包含要在 `CAccessToken` 物件中停用的許可權。

*pPreviousState*<br/>
`CTokenPrivileges` 物件的指標，其中將包含先前的許可權狀態。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="disableprivileges"></a>CAccessToken：:D isablePrivileges

呼叫這個方法，以停用 `CAccessToken` 物件中的一或多個許可權。

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*rPrivileges*<br/>
字串陣列的指標，其中包含要在 `CAccessToken` 物件中停用的許可權。

*pPreviousState*<br/>
`CTokenPrivileges` 物件的指標，其中將包含先前的許可權狀態。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="enableprivilege"></a>CAccessToken：： EnablePrivilege

呼叫這個方法，以在 `CAccessToken` 物件中啟用許可權。

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*pszPrivilege*<br/>
字串的指標，其中包含要在 `CAccessToken` 物件中啟用的許可權。

*pPreviousState*<br/>
`CTokenPrivileges` 物件的指標，其中將包含先前的許可權狀態。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="enableprivileges"></a>CAccessToken：： EnablePrivileges

呼叫這個方法，以啟用 `CAccessToken` 物件中的一或多個許可權。

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*rPrivileges*<br/>
字串陣列的指標，其中包含要在 `CAccessToken` 物件中啟用的許可權。

*pPreviousState*<br/>
`CTokenPrivileges` 物件的指標，其中將包含先前的許可權狀態。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="getdefaultdacl"></a>CAccessToken：： GetDefaultDacl

呼叫這個方法，以傳回 `CAccessToken` 物件的預設 DACL。

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>參數

*pDacl*<br/>
[CDacl 類別](../../atl/reference/cdacl-class.md)物件的指標，它會接收 `CAccessToken` 物件的預設 DACL。

### <a name="return-value"></a>傳回值

如果預設的 DACL 已復原，則傳回 TRUE，否則傳回 FALSE。

##  <a name="geteffectivetoken"></a>CAccessToken：： GetEffectiveToken

呼叫這個方法，讓 `CAccessToken` 物件等於目前線程的作用中存取權杖。

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>參數

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="getgroups"></a>CAccessToken：： GetGroups

呼叫這個方法，以傳回 `CAccessToken` 物件的 token 群組。

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>參數

*pGroups*<br/>
[CTokenGroups 類別](../../atl/reference/ctokengroups-class.md)物件的指標，它會接收群組資訊。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="gethandle"></a>CAccessToken：： GetHandle

呼叫這個方法來抓取存取權杖的控制碼。

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>傳回值

傳回 `CAccessToken` 物件之存取權杖的控制碼。

##  <a name="getimpersonationlevel"></a>CAccessToken：： GetImpersonationLevel

呼叫這個方法，從存取權杖取得模擬層級。

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>參數

*pImpersonationLevel*<br/>
將接收模擬層級資訊的[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)列舉類型的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="getlogonsessionid"></a>CAccessToken：： GetLogonSessionId

呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的登入會話識別碼。

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>參數

*pluid*<br/>
將接收登入會話識別碼之[LUID](/windows/win32/api/winnt/ns-winnt-luid)的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

在 debug build 中，如果*pluid*是不正確值，就會發生判斷提示錯誤。

##  <a name="getlogonsid"></a>CAccessToken：： GetLogonSid

呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的登入 SID。

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
[CSid 類別](../../atl/reference/csid-class.md)物件的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

在 debug build 中，如果*pSid*是不正確值，就會發生判斷提示錯誤。

##  <a name="getowner"></a>CAccessToken：： GetOwner

呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的擁有者。

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
[CSid 類別](../../atl/reference/csid-class.md)物件的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

當此存取權杖生效時，預設會在任何建立的物件上設定擁有者。

##  <a name="getprimarygroup"></a>CAccessToken：： GetPrimaryGroup

呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的主要群組。

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
[CSid 類別](../../atl/reference/csid-class.md)物件的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

群組預設會在此存取權杖生效時建立的任何物件上設定。

##  <a name="getprivileges"></a>CAccessToken：： GetPrivileges

呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的許可權。

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>參數

*pPrivileges*<br/>
[CTokenPrivileges 類別](../../atl/reference/ctokenprivileges-class.md)物件的指標，它會接收許可權。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="getprocesstoken"></a>CAccessToken：： GetProcessToken

呼叫這個方法，以所指處理序的存取權杖初始化 `CAccessToken`。

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>參數

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*hProcess*<br/>
處理已開啟存取權杖的處理序。 如果使用預設值 Null，則會使用目前的進程。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

呼叫[OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32 函數。

##  <a name="getprofile"></a>CAccessToken：： GetProfile

呼叫這個方法，以取得指向與 `CAccessToken` 物件相關聯之使用者設定檔的控制碼。

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>傳回值

傳回指向使用者設定檔的控制碼，如果沒有設定檔存在則傳回 Null。

##  <a name="getsource"></a>CAccessToken：： GetSource

呼叫這個方法以取得 `CAccessToken` 物件的來源。

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>參數

*pSource*<br/>
[TOKEN_SOURCE](/windows/win32/api/winnt/ns-winnt-token_source)結構的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="getstatistics"></a>CAccessToken：： GetStatistics

呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的資訊。

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>參數

*pStatistics*<br/>
[TOKEN_STATISTICS](/windows/win32/api/winnt/ns-winnt-token_statistics)結構的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="getterminalservicessessionid"></a>CAccessToken：： GetTerminalServicesSessionId

呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的終端機服務會話識別碼。

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>參數

*pdwSessionId*<br/>
終端機服務會話識別碼。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="getthreadtoken"></a>CAccessToken：： GetThreadToken

呼叫這個方法，以使用來自給定執行緒的 token 來初始化 `CAccessToken`。

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
已開啟其存取權杖之執行緒的控制碼。

*bOpenAsSelf*<br/>
指出是否要針對呼叫 `GetThreadToken` 方法的執行緒安全性內容，或針對呼叫執行緒之進程的安全性內容進行存取檢查。

如果此參數為 FALSE，則會使用呼叫執行緒的安全性內容來執行存取檢查。 如果執行緒正在模擬用戶端，此安全性內容就可能是用戶端進程的其中一個。 如果此參數為 TRUE，則會使用呼叫執行緒之進程的安全性內容來進行存取檢查。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="gettokenid"></a>CAccessToken：： GetTokenId

呼叫這個方法，以取得與 `CAccessToken` 物件相關聯的 Token 識別碼。

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>參數

*pluid*<br/>
將接收 Token 識別碼之[LUID](/windows/win32/api/winnt/ns-winnt-luid)的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="gettype"></a>CAccessToken：： GetType

呼叫這個方法，以取得 `CAccessToken` 物件的 token 類型。

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>參數

*pType*<br/>
成功時， [TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type)變數的位址會接收 TOKEN 的類型。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

TOKEN_TYPE 列舉類型包含可區別主要權杖和模擬權杖的值。

##  <a name="getuser"></a>CAccessToken：： GetUser

呼叫這個方法，以識別與 `CAccessToken` 物件相關聯的使用者。

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
[CSid 類別](../../atl/reference/csid-class.md)物件的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

##  <a name="hkeycurrentuser"></a>CAccessToken：： HKeyCurrentUser

呼叫這個方法，以取得指向與 `CAccessToken` 物件相關聯之使用者設定檔的控制碼。

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>傳回值

傳回指向使用者設定檔的控制碼，如果沒有設定檔存在則傳回 Null。

##  <a name="impersonate"></a>CAccessToken：：模擬

呼叫這個方法，將模擬 `CAccessToken` 指派給執行緒。

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*hThread*<br/>
要指派模擬權杖的執行緒控制碼。 這個控制碼必須以 TOKEN_IMPERSONATE 存取權限開啟。 如果*hThread*為 Null，則方法會使執行緒停止使用模擬 token。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

在 [偵錯工具] 組建中，如果 `CAccessToken` 沒有標記的有效指標，就會發生判斷提示錯誤。

[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用於自動還原模擬的存取權杖。

##  <a name="impersonateloggedonuser"></a>CAccessToken：： ImpersonateLoggedOnUser

呼叫此方法可讓呼叫執行緒模擬已登入使用者的安全性內容。

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

> [!IMPORTANT]
>  如果模擬函式的呼叫因任何原因而失敗，則不會模擬用戶端，並且會在進行呼叫之進程的安全性內容中提出用戶端要求。 如果進程是以高許可權帳戶或系統管理群組成員的身分執行，則使用者可能會在不允許的情況下執行動作。 因此，應一律確認此函數的傳回值。

##  <a name="istokenrestricted"></a>CAccessToken：： IsTokenRestricted

呼叫這個方法來測試 `CAccessToken` 物件是否包含受限制的 Sid 清單。

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>傳回值

如果物件包含限制 Sid 的清單，則傳回 TRUE，如果沒有限制 Sid，或方法失敗，則傳回 FALSE。

##  <a name="loaduserprofile"></a>CAccessToken：： LoadUserProfile

呼叫這個方法，載入與 `CAccessToken` 物件相關聯的使用者設定檔。

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

在 [偵錯工具] 組建中，如果 `CAccessToken` 不包含有效的 token，或使用者設定檔已經存在，就會發生判斷提示錯誤。

##  <a name="logonuser"></a>CAccessToken：： LogonUser

呼叫這個方法，為與指定認證相關聯的使用者建立登入會話。

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
指定使用者名稱之以 null 終止之字串的指標。 這是用來登入的使用者帳戶名稱。

*pszDomain*<br/>
以 null 結束的字串指標，指定其帳戶資料庫包含*pszUserName*帳戶的網域或伺服器名稱。

*pszPassword*<br/>
以 null 結束的字串指標，指定*pszUserName*所指定之使用者帳戶的純文字密碼。

*dwLogonType*<br/>
指定要執行的登入操作類型。 如需詳細資訊，請參閱[LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) 。

*dwLogonProvider*<br/>
指定登入提供者。 如需詳細資訊，請參閱[LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) 。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

登入所產生的存取權杖將會與 `CAccessToken`相關聯。 若要讓此方法成功，`CAccessToken` 物件必須持有 SE_TCB_NAME 許可權，將持有者識別為信任的電腦基底的一部分。 如需有關必要許可權的詳細資訊，請參閱[LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) 。

##  <a name="opencomclienttoken"></a>CAccessToken：： OpenCOMClientToken

從 COM 伺服器內呼叫此方法，以處理來自用戶端的呼叫，以使用來自 COM 用戶端的存取權杖來初始化 `CAccessToken`。

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
若為 TRUE，當此呼叫成功完成時，目前的執行緒會模擬呼叫的 COM 用戶端。 若為 FALSE，將會開啟存取權杖，但當此呼叫完成時，執行緒將不會有模擬 token。

*bOpenAsSelf*<br/>
指出是否要針對呼叫[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的執行緒安全性內容，或針對呼叫執行緒之進程的安全性內容進行存取檢查。

如果此參數為 FALSE，則會使用呼叫執行緒的安全性內容來執行存取檢查。 如果執行緒正在模擬用戶端，此安全性內容就可能是用戶端進程的其中一個。 如果此參數為 TRUE，則會使用呼叫執行緒之進程的安全性內容來進行存取檢查。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用於自動還原藉由將*bImpersonate*旗標設定為 TRUE 而建立的模擬存取權杖。

##  <a name="opennamedpipeclienttoken"></a>CAccessToken：： OpenNamedPipeClientToken

從伺服器內呼叫此方法，透過具名管道取得要求，使用來自用戶端的存取權杖初始化 `CAccessToken`。

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>參數

*hPipe*<br/>
具名管道的控制碼。

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*bImpersonate*<br/>
若為 TRUE，當此呼叫成功完成時，目前的執行緒會模擬呼叫管道用戶端。 若為 FALSE，將會開啟存取權杖，但當此呼叫完成時，執行緒將不會有模擬 token。

*bOpenAsSelf*<br/>
指出是否要針對呼叫[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的執行緒安全性內容，或針對呼叫執行緒之進程的安全性內容進行存取檢查。

如果此參數為 FALSE，則會使用呼叫執行緒的安全性內容來執行存取檢查。 如果執行緒正在模擬用戶端，此安全性內容就可能是用戶端進程的其中一個。 如果此參數為 TRUE，則會使用呼叫執行緒之進程的安全性內容來進行存取檢查。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用於自動還原藉由將*bImpersonate*旗標設定為 TRUE 而建立的模擬存取權杖。

##  <a name="openrpcclienttoken"></a>CAccessToken：： OpenRPCClientToken

從處理 RPC 用戶端呼叫的伺服器內呼叫此方法，以使用來自用戶端的存取權杖來初始化 `CAccessToken`。

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>參數

*BindingHandle*<br/>
伺服器上的系結控制碼，代表用戶端的系結。

*dwDesiredAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*bImpersonate*<br/>
若為 TRUE，當此呼叫成功完成時，目前的執行緒會模擬呼叫 RPC 用戶端。 若為 FALSE，將會開啟存取權杖，但當此呼叫完成時，執行緒將不會有模擬 token。

*bOpenAsSelf*<br/>
指出是否要針對呼叫[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的執行緒安全性內容，或針對呼叫執行緒之進程的安全性內容進行存取檢查。

如果此參數為 FALSE，則會使用呼叫執行緒的安全性內容來執行存取檢查。 如果執行緒正在模擬用戶端，此安全性內容就可能是用戶端進程的其中一個。 如果此參數為 TRUE，則會使用呼叫執行緒之進程的安全性內容來進行存取檢查。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用於自動還原藉由將*bImpersonate*旗標設定為 TRUE 而建立的模擬存取權杖。

##  <a name="openthreadtoken"></a>CAccessToken：： OpenThreadToken

呼叫這個方法以設定模擬層級，然後使用來自給定執行緒的權杖初始化 `CAccessToken`。

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
若為 TRUE，則在此方法完成後，執行緒會保留在要求的模擬層級。 如果為 FALSE，則執行緒會還原為其原始模擬層級。

*bOpenAsSelf*<br/>
指出是否要針對呼叫[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的執行緒安全性內容，或針對呼叫執行緒之進程的安全性內容進行存取檢查。

如果此參數為 FALSE，則會使用呼叫執行緒的安全性內容來執行存取檢查。 如果執行緒正在模擬用戶端，此安全性內容就可能是用戶端進程的其中一個。 如果此參數為 TRUE，則會使用呼叫執行緒之進程的安全性內容來進行存取檢查。

*sil*<br/>
指定提供權杖模擬層級的[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)列舉類型。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

`OpenThreadToken` 類似于[CAccessToken：： GetThreadToken](#getthreadtoken)，但會先設定模擬層級，再從執行緒的存取權杖初始化 `CAccessToken`。

[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)可用於自動還原藉由將*bImpersonate*旗標設定為 TRUE 而建立的模擬存取權杖。

##  <a name="privilegecheck"></a>CAccessToken：:P rivilegeCheck

呼叫這個方法，以判斷是否在 `CAccessToken` 物件中啟用一組指定的許可權。

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>參數

*RequiredPrivileges*<br/>
[PRIVILEGE_SET](/windows/win32/api/winnt/ns-winnt-privilege_set)結構的指標。

*pbResult*<br/>
此方法所設定之值的指標，表示 `CAccessToken` 物件中是否已啟用任何或所有指定的許可權。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

當 `PrivilegeCheck` 傳回時，如果已啟用對應的許可權，則會將每個[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)結構的 `Attributes` 成員設定為 SE_PRIVILEGE_USED_FOR_ACCESS。 這個方法會呼叫[PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32 函數。

##  <a name="revert"></a>CAccessToken：： Revert

呼叫這個方法，以停止執行緒使用模擬 token。

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>參數

*hThread*<br/>
要從模擬還原之執行緒的控制碼。 如果*hThread*為 Null，則會假設為目前的執行緒。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

模擬權杖的回復可以使用[CAutoRevertImpersonation 類別](../../atl/reference/cautorevertimpersonation-class.md)自動執行。

##  <a name="setdefaultdacl"></a>CAccessToken：： SetDefaultDacl

呼叫這個方法，以設定 `CAccessToken` 物件的預設 DACL。

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>參數

*rDacl*<br/>
新的預設[CDacl 類別](../../atl/reference/cdacl-class.md)資訊。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

預設的 DACL 是當使用此存取權杖來建立新物件時，預設會使用的 DACL。

##  <a name="setowner"></a>CAccessToken：： SetOwner

呼叫這個方法來設定 `CAccessToken` 物件的擁有者。

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
包含擁有者資訊的[CSid 類別](../../atl/reference/csid-class.md)物件。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

「擁有者」是預設的擁有者，用於在此存取權杖生效時建立的新物件。

##  <a name="setprimarygroup"></a>CAccessToken：： SetPrimaryGroup

呼叫這個方法，以設定 `CAccessToken` 物件的主要群組。

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
包含主要群組資訊的[CSid 類別](../../atl/reference/csid-class.md)物件。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

主要群組是在此存取權杖生效時，所建立新物件的預設群組。

## <a name="see-also"></a>另請參閱

[ATLSecurity 範例](../../overview/visual-cpp-samples.md)<br/>
[存取權杖](/windows/win32/SecAuthZ/access-tokens)<br/>
[類別總覽](../../atl/atl-class-overview.md)
