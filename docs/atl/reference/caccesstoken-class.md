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
ms.openlocfilehash: f7a2ee2f9d633c1ed743621eec5b2f7cc04c0e0b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748822"
---
# <a name="caccesstoken-class"></a>CAccessToken 類別

此類是訪問權杖的包裝器。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAccessToken
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAccessToken::*CAccessToken](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAccessToken::附加](#attach)|調用此方法以取得給定訪問權杖句柄的擁有權。|
|[CAccessToken::檢查權杖成員資格](#checktokenmembership)|呼叫此方法以確定`CAccessToken`物件中是否啟用了指定的 SID。|
|[CAccessToken:: 建立模擬權杖](#createimpersonationtoken)|呼叫此方法以創建新的模擬存取權杖。|
|[CAccessToken::建立主要權杖](#createprimarytoken)|調用此方法以創建新的主權杖。|
|[CAccessToken::建立行程使用者](#createprocessasuser)|調用此方法以創建在`CAccessToken`物件表示的使用者的安全上下文中運行的新進程。|
|[CAccessToken::建立受限權杖](#createrestrictedtoken)|調用此方法以創建新的受限`CAccessToken`物件。|
|[CAccessToken::Detach](#detach)|調用此方法以撤銷訪問權杖的擁有權。|
|[CAccessToken::D可特權](#disableprivilege)|調用此方法以禁用物件中`CAccessToken`的特權。|
|[CAccessToken::D可特權](#disableprivileges)|調用此方法以禁用`CAccessToken`物件中的一個或多個許可權。|
|[CAccessToken::啟用特權](#enableprivilege)|調用此方法以在`CAccessToken`物件中啟用許可權。|
|[CAccessToken::啟用特權](#enableprivileges)|調用此方法以啟用物件中的`CAccessToken`一個或多個許可權。|
|[CAccessToken:取得預設Dacl](#getdefaultdacl)|調用此方法以返回`CAccessToken`物件的預設 DACL。|
|[CAccessToken:取得有效權杖](#geteffectivetoken)|呼叫此方法以獲取等於當前`CAccessToken`線程有效的訪問權杖的物件。|
|[CAccessToken:取得群組](#getgroups)|調用此方法以返回`CAccessToken`物件的權杖組。|
|[CAccessToken:取得句柄](#gethandle)|調用此方法以檢索訪問權杖的句柄。|
|[CAccessToken:取得模擬層級](#getimpersonationlevel)|調用此方法從訪問權杖獲取類比級別。|
|[CAccessToken:取得登入工作階段 Id](#getlogonsessionid)|呼叫此方法以獲取與`CAccessToken`物件關聯的登錄會話 ID。|
|[CAccessToken:取得登入 Sid](#getlogonsid)|呼叫此方法以獲取與`CAccessToken`物件關聯的登錄 SID。|
|[CAccessToken:取得擁有者](#getowner)|調用此方法以獲取與`CAccessToken`對象關聯的擁有者。|
|[CAccessToken:取得主要組](#getprimarygroup)|調用此方法獲取與`CAccessToken`物件關聯的主組。|
|[CAccessToken:取得特權](#getprivileges)|調用此方法獲取與`CAccessToken`對象關聯的許可權。|
|[CAccessToken::取得行程權杖](#getprocesstoken)|呼叫這個方法，以所指處理序的存取權杖初始化 `CAccessToken`。|
|[CAccessToken:取得設定檔](#getprofile)|呼叫此方法以獲取指向與物件關聯的使用者設定檔的`CAccessToken`句柄。|
|[CAccessToken:取得來源](#getsource)|調用此方法以獲取`CAccessToken`物件的源。|
|[CAccessToken:取得統計資訊](#getstatistics)|調用此方法以獲取有關`CAccessToken`物件的資訊。|
|[CAccessToken::取得終端服務會話Id](#getterminalservicessessionid)|呼叫此方法獲取與`CAccessToken`物件關聯的終端服務會話 ID。|
|[CAccessToken:抓取緒權杖](#getthreadtoken)|呼叫此方法以使用給定緒中的`CAccessToken`權杖初始化 。|
|[CAccessToken::取得權杖 ID](#gettokenid)|呼叫此方法以獲取與`CAccessToken`物件關聯的權杖 ID。|
|[CAccessToken:取得類型](#gettype)|調用此方法以獲取`CAccessToken`物件的權杖類型。|
|[CAccessToken:取得使用者](#getuser)|調用此方法以標識與`CAccessToken`物件關聯的使用者。|
|[CAccessToken::HKeycurrentUser](#hkeycurrentuser)|呼叫此方法以獲取指向與物件關聯的使用者設定檔的`CAccessToken`句柄。|
|[CAccessToken:模擬](#impersonate)|調用此方法以將類`CAccessToken`比分配給線程。|
|[CAccessToken::模擬登錄使用者](#impersonateloggedonuser)|調用此方法以允許調用線程類比登錄使用者的安全上下文。|
|[CAccessToken::受限制](#istokenrestricted)|調用此方法以測試`CAccessToken`物件是否包含受限 S 的清單。|
|[CAccessToken::載入使用者設定檔](#loaduserprofile)|呼叫此方法以載入與`CAccessToken`物件關聯的使用者配置檔。|
|[CAccessToken::登錄使用者](#logonuser)|調用此方法為與給定憑據關聯的用戶創建登錄會話。|
|[CAccessToken::打開COM用戶端權杖](#opencomclienttoken)|從處理來自用戶端的電話的 COM 伺服器內呼叫此方法,`CAccessToken`以便使用 COM 用戶端的存取權杖初始化 。|
|[CAccessToken::開啟命名導管客戶端權杖](#opennamedpipeclienttoken)|從伺服器內呼叫此方法,透過命名導管取得請求,以便使用客戶端的存`CAccessToken`取權杖 初始化 。|
|[CAccessToken::打開RPC客戶端權杖](#openrpcclienttoken)|從伺服器內呼叫此方法,以處理來自 RPC 客戶端的呼`CAccessToken`叫,以便使用客戶端的存取權杖初始化 。|
|[CAccessToken::開啟線程權杖](#openthreadtoken)|呼叫此方法以設定模擬等級,然後使用給定線程中的權杖初始化`CAccessToken`。|
|[CAccessToken::P里維萊格檢查](#privilegecheck)|呼叫此方法以確定物件中`CAccessToken`是否啟用了指定的許可權集。|
|[CAccessToken::恢復](#revert)|調用此方法以阻止使用類比權杖的線程。|
|[CAccessToken::設定預設Dacl](#setdefaultdacl)|呼叫此方法以設定`CAccessToken`物件的預設 DACL。|
|[CAccessToken::SetOwner](#setowner)|調用此方法以設置`CAccessToken`物件的擁有者。|
|[CAccessToken::設定主要組](#setprimarygroup)|調用此方法以設置`CAccessToken`物件的主組。|

## <a name="remarks"></a>備註

[訪問權杖](/windows/win32/SecAuthZ/access-tokens)是描述進程或線程的安全上下文並分配給登錄到 Windows 系統的每個使用者的物件。

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="caccesstokenattach"></a><a name="attach"></a>CAccessToken::附加

調用此方法以取得給定訪問權杖句柄的擁有權。

```cpp
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>參數

*hToken*<br/>
訪問權杖的句柄。

### <a name="remarks"></a>備註

在調試生成中,如果物件已擁有訪問令牌`CAccessToken`的擁有權,則會發生斷言錯誤。

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a>CAccessToken::*CAccessToken

解構函式。

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>備註

釋放所有分配的資源。

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a>CAccessToken::檢查權杖成員資格

呼叫此方法以確定`CAccessToken`物件中是否啟用了指定的 SID。

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
對[CSid 類](../../atl/reference/csid-class.md)物件的引用。

*pbIs成員*<br/>
指向接收檢查結果的變數的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

該方法`CheckTokenMembership`檢查存取權杖的使用者和組SID中是否存在SID。 如果 SID 存在並且具有SE_GROUP_ENABLED屬性,*則 pbIs成員*設置為 TRUE;如果 SID 具有 SE_GROUP_ENABLED屬性,則 pbIs 會員將設置為 TRUE;否則,它將設置為 FALSE。

在調試生成中,如果*pbIs會員*不是有效的指標,則會發生斷言錯誤。

> [!NOTE]
> 該`CAccessToken`物件必須是類比權杖,而不是主權杖。

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a>CAccessToken:: 建立模擬權杖

呼叫此方法以建立模擬存取權杖。

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>參數

*皮條 客*<br/>
指向新`CAccessToken`物件的指標。

*Sil*<br/>
指定提供新權杖的類比等級的[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)枚舉類型。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

`CreateImpersonationToken`呼叫[重複權杖](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken)以建立新的模擬權杖。

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a>CAccessToken::建立主要權杖

調用此方法以創建新的主權杖。

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pPri*<br/>
指向新`CAccessToken`物件的指標。

*dwddAccess*<br/>
指定新權杖的請求訪問許可權。 默認的 MAXIMUM_ALLOWED 請求對調用方有效的所有訪問許可權。 有關存取權限的更多,請參閱[存取權限和存取遮罩](/windows/win32/SecAuthZ/access-rights-and-access-masks)。

*pToken 屬性*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構的指標,該結構指定新令牌的安全描述符,並確定子進程是否可以繼承權杖。 如果*pTokenAttributes*為 NULL,則令牌獲取預設安全描述符,並且無法繼承句柄。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

`CreatePrimaryToken`呼叫[重複權杖Ex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex)創建新的主權杖。

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a>CAccessToken::建立行程使用者

調用此方法以創建在`CAccessToken`物件表示的使用者的安全上下文中運行的新進程。

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

*p 應用程式名稱*<br/>
指定要執行的模組的 null 的標頭針。 此參數可能不是 NULL。

*pCommandLine*<br/>
指定要執行的命令列的 null 的標記。

*p 行程資訊*<br/>
指向接收有關新進程的標識資訊[的PROCESS_INFORMATION結構](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information)的指標。

*pStartup資訊*<br/>
指向[STARTUPINFO](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow)結構的指標,該結構指定新進程的主視窗的顯示方式。

*dw創造標誌*<br/>
指定控制優先權類和進程創建的其他標誌。 有關標誌清單,請參閱 Win32 函數[「創建行程AsUser」。。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw)

*bLoad 設定檔*<br/>
如果為 TRUE,則使用者的設定檔將載入[LoadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew)。

*p 行程屬性*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構的指標,該結構指定新進程的安全描述符,並確定子進程是否可以繼承返回的句柄。 如果*pProcessAttributes*為 NULL,則行程將獲取預設安全描述符,並且無法繼承句柄。

*pThread屬性*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構的指標,該結構指定新線程的安全描述符,並確定子進程是否可以繼承返回的句柄。 如果*pThreadAttributes*為 NULL,則執行緒將取得預設安全描述符,並且無法繼承句柄。

*b繼承*<br/>
指示新進程是否從調用進程繼承句柄。 如果為 TRUE,則調用進程中的每個可繼承打開句柄都由新進程繼承。 繼承的句柄具有與原始句柄相同的值和訪問許可權。

*pCurrentDirectory*<br/>
指向 null 連接端的字串的指標,該字串指定新行程的當前驅動器和目錄。 字串必須是包含驅動器號的完整路徑。 如果此參數為 NULL,則新進程將具有與調用進程相同的當前驅動器和目錄。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

`CreateProcessAsUser`使用`CreateProcessAsUser`Win32 函數`CAccessToken`創建在 物件表示的使用者的安全上下文中運行的新進程。 有關所需參數的完整討論,請參閱[CreateProcessAsUser 函數](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw)的說明。

要讓此方法成功,`CAccessToken`對象必須保留 AssignPrimaryToken(除非它是受限權杖)和「增加配額」許可權。

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a>CAccessToken::建立受限權杖

調用此方法以創建新的受限`CAccessToken`物件。

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>參數

*p受限權杖*<br/>
新的受限`CAccessToken`物件。

*Sidsto 停用*<br/>
指定`CTokenGroups`僅拒絕 S 的物件。

*Sidsto 限制*<br/>
`CTokenGroups`指定限制 S 的物件。

*要刪除的權限*<br/>
指定`CTokenPrivileges`在受限權杖中刪除的許可權的物件。 預設值創建一個空物件。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

`CreateRestrictedToken`使用[Create 限制權杖](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken)Win32`CAccessToken`函數建立 具有限制的新物件。

> [!IMPORTANT]
> 使用`CreateRestrictedToken`時,請確保以下內容:現有權杖有效(使用者未輸入)和*SidsTo 禁用*和*特權刪除*都有效(並且使用者不輸入)。 如果該方法返回 FALSE,則拒絕功能。

## <a name="caccesstokendetach"></a><a name="detach"></a>CAccessToken::Detach

調用此方法以撤銷訪問權杖的擁有權。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>傳回值

將句柄返回到已分離`CAccessToken`的句柄。

### <a name="remarks"></a>備註

此方法撤消`CAccessToken`訪問權杖的擁有權。

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a>CAccessToken::D可特權

調用此方法以禁用物件中`CAccessToken`的特權。

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*psz特權*<br/>
指向包含要在物件中禁用的許可權的字串的`CAccessToken`指標。

*p 上一個狀態*<br/>
指向將包含`CTokenPrivileges`許可權的上一個狀態的物件的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a>CAccessToken::D可特權

調用此方法以禁用`CAccessToken`物件中的一個或多個許可權。

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*r特權*<br/>
指向包含要在`CAccessToken`物件中禁用的許可權的字串陣列的指標。

*p 上一個狀態*<br/>
指向將包含`CTokenPrivileges`許可權的上一個狀態的物件的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a>CAccessToken::啟用特權

調用此方法以在`CAccessToken`物件中啟用許可權。

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*psz特權*<br/>
指向包含要在物件中啟用的權限`CAccessToken`的字串的指標。

*p 上一個狀態*<br/>
指向將包含`CTokenPrivileges`許可權的上一個狀態的物件的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a>CAccessToken::啟用特權

調用此方法以啟用物件中的`CAccessToken`一個或多個許可權。

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>參數

*r特權*<br/>
指向包含在`CAccessToken`物件中啟用的權限的字串陣列。

*p 上一個狀態*<br/>
指向將包含`CTokenPrivileges`許可權的上一個狀態的物件的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a>CAccessToken:取得預設Dacl

調用此方法以返回`CAccessToken`物件的預設 DACL。

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>參數

*pDacl*<br/>
指向[CDacl 類別](../../atl/reference/cdacl-class.md)的指標,`CAccessToken`該物件將接收物件的預設 DACL。

### <a name="return-value"></a>傳回值

如果預設 DACL 已恢復,則傳回 TRUE,否則返回 FALSE。

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a>CAccessToken:取得有效權杖

呼叫此方法以獲取等於當前`CAccessToken`線程有效的訪問權杖的物件。

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>參數

*dwddAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a>CAccessToken:取得群組

調用此方法以返回`CAccessToken`物件的權杖組。

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>參數

*p組*<br/>
指向將接收組資訊的[CTokenGroup 類](../../atl/reference/ctokengroups-class.md)物件。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokengethandle"></a><a name="gethandle"></a>CAccessToken:取得句柄

調用此方法以檢索訪問權杖的句柄。

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>傳回值

返回對象訪問權杖`CAccessToken`的句柄。

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a>CAccessToken:取得模擬層級

調用此方法從訪問權杖獲取類比級別。

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>參數

*p 模擬等級*<br/>
指向[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)枚舉類型的指標,該類型將接收模擬級別資訊。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a>CAccessToken:取得登入工作階段 Id

呼叫此方法以獲取與`CAccessToken`物件關聯的登錄會話 ID。

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>參數

*普盧伊德*<br/>
指向將接收登錄會話 ID 的[LUID](/windows/win32/api/winnt/ns-winnt-luid)的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

在調試生成中,如果*pluid*是無效值,則會發生斷言錯誤。

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a>CAccessToken:取得登入 Sid

呼叫此方法以獲取與`CAccessToken`物件關聯的登錄 SID。

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指向[CSid 類](../../atl/reference/csid-class.md)物件的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

在調試生成中,如果*pSid*是無效值,則會發生斷言錯誤。

## <a name="caccesstokengetowner"></a><a name="getowner"></a>CAccessToken:取得擁有者

調用此方法以獲取與`CAccessToken`對象關聯的擁有者。

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指向[CSid 類](../../atl/reference/csid-class.md)物件的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

默認情況下,將在此訪問權杖生效時創建的任何物件上設置擁有者。

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a>CAccessToken:取得主要組

調用此方法獲取與`CAccessToken`物件關聯的主組。

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指向[CSid 類](../../atl/reference/csid-class.md)物件的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

默認情況下,該組將設置在此訪問權杖生效時創建的任何物件上。

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a>CAccessToken:取得特權

調用此方法獲取與`CAccessToken`對象關聯的許可權。

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>參數

*p權限*<br/>
指向將收到特權[的 CToken 特權類](../../atl/reference/ctokenprivileges-class.md)物件。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a>CAccessToken::取得行程權杖

呼叫這個方法，以所指處理序的存取權杖初始化 `CAccessToken`。

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>參數

*dwddAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*h行程*<br/>
處理已開啟存取權杖的處理序。 如果使用 NULL 的預設值,則使用當前過程。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

調用[OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32 功能。

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a>CAccessToken:取得設定檔

呼叫此方法以獲取指向與物件關聯的使用者設定檔的`CAccessToken`句柄。

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>傳回值

傳回指向使用者設定檔的句柄,如果不存在設定檔,則傳回 NULL。

## <a name="caccesstokengetsource"></a><a name="getsource"></a>CAccessToken:取得來源

調用此方法以獲取`CAccessToken`物件的源。

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>參數

*p來源*<br/>
指向[TOKEN_SOURCE](/windows/win32/api/winnt/ns-winnt-token_source)結構的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a>CAccessToken:取得統計資訊

調用此方法以獲取有關`CAccessToken`物件的資訊。

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>參數

*p 統計*<br/>
指向[TOKEN_STATISTICS](/windows/win32/api/winnt/ns-winnt-token_statistics)結構的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a>CAccessToken::取得終端服務會話Id

呼叫此方法獲取與`CAccessToken`物件關聯的終端服務會話 ID。

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>參數

*pdwSessionId*<br/>
終端服務會話 ID。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a>CAccessToken:抓取緒權杖

呼叫此方法以使用給定緒中的`CAccessToken`權杖初始化 。

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>參數

*dwddAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*hThread*<br/>
處理其訪問權杖打開的線程。

*bOpenAsSelf*<br/>
指示是針對調用`GetThreadToken`方法的線程的安全上下文或調用線程的進程的安全上下文進行訪問檢查。

如果此參數為 FALSE,則使用呼叫線程的安全上下文執行訪問檢查。 如果線程正在模擬用戶端,則此安全上下文可以是客戶端進程的安全上下文。 如果此參數為 TRUE,則使用呼叫線程的進程的安全上下文進行訪問檢查。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a>CAccessToken::取得權杖 ID

呼叫此方法以獲取與`CAccessToken`物件關聯的權杖 ID。

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>參數

*普盧伊德*<br/>
指向將接收權杖 ID 的[LUID](/windows/win32/api/winnt/ns-winnt-luid)的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokengettype"></a><a name="gettype"></a>CAccessToken:取得類型

調用此方法以獲取`CAccessToken`物件的權杖類型。

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>參數

*p 型態*<br/>
[TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type)變數的位址,在成功時,該變數接收令牌的類型。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

TOKEN_TYPE枚舉類型包含區分主權杖和類比權杖的值。

## <a name="caccesstokengetuser"></a><a name="getuser"></a>CAccessToken:取得使用者

調用此方法以標識與`CAccessToken`物件關聯的使用者。

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>參數

*pSid*<br/>
指向[CSid 類](../../atl/reference/csid-class.md)物件的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a>CAccessToken::HKeycurrentUser

呼叫此方法以獲取指向與物件關聯的使用者設定檔的`CAccessToken`句柄。

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>傳回值

傳回指向使用者設定檔的句柄,如果不存在設定檔,則傳回 NULL。

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a>CAccessToken:模擬

調用此方法以將類`CAccessToken`比分配給線程。

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*hThread*<br/>
將搖桿將模擬的權號來分配 。 此句柄必須已打開,具有TOKEN_IMPERSONATE訪問許可權。 如果*hThread*為 NULL,則該方法會導致線程停止使用類比令牌。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

在調試生成中,如果沒有`CAccessToken`指向令牌的有效指標,將發生斷言錯誤。

[CAuto 還原類比類](../../atl/reference/cautorevertimpersonation-class.md)可用於自動還原模擬訪問權杖。

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a>CAccessToken::模擬登錄使用者

調用此方法以允許調用線程類比登錄使用者的安全上下文。

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

> [!IMPORTANT]
> 如果對類比函數的調用由於任何原因失敗,則用戶端不會類比,並且用戶端請求是在發出調用的進程的安全上下文中進行的。 如果進程以高度特權帳戶或管理組的成員運行,則使用者可能能夠執行否則將不允許執行的操作。 因此,應始終確認此函數的返回值。

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a>CAccessToken::受限制

調用此方法以測試`CAccessToken`物件是否包含受限 S 的清單。

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>傳回值

如果物件包含限制 S 的清單,則傳回 TRUE;如果沒有限制 SID 或方法失敗,則為 FALSE。

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a>CAccessToken::載入使用者設定檔

呼叫此方法以載入與`CAccessToken`物件關聯的使用者配置檔。

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

在調試生成中,如果`CAccessToken`不包含有效的權杖,或者使用者配置檔已存在,則會發生斷言錯誤。

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a>CAccessToken::登錄使用者

調用此方法為與給定憑據關聯的用戶創建登錄會話。

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>參數

*pszUser 名稱*<br/>
指定使用者名稱的 null 的字串的指標。 這是要登錄的使用者帳戶的名稱。

*pszDomain*<br/>
指向 null 終止字串的指標,該字串指定其帳戶資料庫包含*pszUserName*帳戶的域或伺服器的名稱。

*psz密碼*<br/>
指向 null 終止字串的指標,該字串指定*pszUserName*指定的使用者帳戶的明文密碼。

*dwLogon 類型*<br/>
指定要執行的登入操作的類型。 有關詳細資訊[,請參閱登入使用者](/windows/win32/api/winbase/nf-winbase-logonuserw)。

*dwLogon 提供者*<br/>
指定登錄提供程式。 有關詳細資訊[,請參閱登入使用者](/windows/win32/api/winbase/nf-winbase-logonuserw)。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

登入產生的存取權杖將與`CAccessToken`相關聯 。 要使此方法成功,`CAccessToken`物件必須保留SE_TCB_NAME許可權,將持有者標識為受信任的計算機基礎的一部分。 有關需要權限的詳細資訊,請參考[登入使用者](/windows/win32/api/winbase/nf-winbase-logonuserw)。

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a>CAccessToken::打開COM用戶端權杖

從處理來自用戶端的電話的 COM 伺服器內呼叫此方法,`CAccessToken`以便使用 COM 用戶端的存取權杖初始化 。

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>參數

*dwddAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*B 模擬*<br/>
如果為 TRUE,則如果此調用成功完成,則當前線程將類比呼叫 COM 用戶端。 如果 FALSE,將打開訪問權杖,但線程將在此調用完成時沒有類比權杖。

*bOpenAsSelf*<br/>
指示是針對調用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的線程的安全上下文或調用線程進程的安全上下文進行訪問檢查。

如果此參數為 FALSE,則使用呼叫線程的安全上下文執行訪問檢查。 如果線程正在模擬用戶端,則此安全上下文可以是客戶端進程的安全上下文。 如果此參數為 TRUE,則使用呼叫線程的進程的安全上下文進行訪問檢查。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

[CAuto 還原類比類](../../atl/reference/cautorevertimpersonation-class.md)可用於透過將*bImpersonate*標誌設定為 TRUE 自動還原建立的模擬存取權杖。

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a>CAccessToken::開啟命名導管客戶端權杖

從伺服器內呼叫此方法,透過命名導管取得請求,以便使用客戶端的存`CAccessToken`取權杖 初始化 。

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>參數

*hPipe*<br/>
處理命名管道。

*dwddAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*B 模擬*<br/>
如果 TRUE,如果此調用成功完成,則當前線程將類比調用管道用戶端。 如果 FALSE,將打開訪問權杖,但線程將在此調用完成時沒有類比權杖。

*bOpenAsSelf*<br/>
指示是針對調用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的線程的安全上下文或調用線程進程的安全上下文進行訪問檢查。

如果此參數為 FALSE,則使用呼叫線程的安全上下文執行訪問檢查。 如果線程正在模擬用戶端,則此安全上下文可以是客戶端進程的安全上下文。 如果此參數為 TRUE,則使用呼叫線程的進程的安全上下文進行訪問檢查。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

[CAuto 還原類比類](../../atl/reference/cautorevertimpersonation-class.md)可用於透過將*bImpersonate*標誌設定為 TRUE 自動還原建立的模擬存取權杖。

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a>CAccessToken::打開RPC客戶端權杖

從伺服器內呼叫此方法,以處理來自 RPC 客戶端的呼`CAccessToken`叫,以便使用客戶端的存取權杖初始化 。

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>參數

*繫結句柄*<br/>
伺服器上表示對用戶端綁定的綁定句柄。

*dwddAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*B 模擬*<br/>
如果為 TRUE,則如果此調用成功完成,則當前線程將類比調用 RPC 用戶端。 如果 FALSE,將打開訪問權杖,但線程將在此調用完成時沒有類比權杖。

*bOpenAsSelf*<br/>
指示是針對調用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的線程的安全上下文或調用線程進程的安全上下文進行訪問檢查。

如果此參數為 FALSE,則使用呼叫線程的安全上下文執行訪問檢查。 如果線程正在模擬用戶端,則此安全上下文可以是客戶端進程的安全上下文。 如果此參數為 TRUE,則使用呼叫線程的進程的安全上下文進行訪問檢查。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

[CAuto 還原類比類](../../atl/reference/cautorevertimpersonation-class.md)可用於透過將*bImpersonate*標誌設定為 TRUE 自動還原建立的模擬存取權杖。

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a>CAccessToken::開啟線程權杖

呼叫此方法以設定模擬等級,然後使用給定線程中的權杖初始化`CAccessToken`。

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>參數

*dwddAccess*<br/>
指定存取遮罩，用以指定對存取權杖的必要存取類型。 這些必要的存取類型會與權杖的 DACL 比較，以決定要授與或拒絕的存取。

*B 模擬*<br/>
如果為 TRUE,則在此方法完成後,線程將留在請求的類比級別。 如果 FALSE,線程將恢復為其原始模擬級別。

*bOpenAsSelf*<br/>
指示是針對調用[GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)方法的線程的安全上下文或調用線程進程的安全上下文進行訪問檢查。

如果此參數為 FALSE,則使用呼叫線程的安全上下文執行訪問檢查。 如果線程正在模擬用戶端,則此安全上下文可以是客戶端進程的安全上下文。 如果此參數為 TRUE,則使用呼叫線程的進程的安全上下文進行訪問檢查。

*Sil*<br/>
指定提供權杖類比等級的[SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level)枚舉類型。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

`OpenThreadToken`類似於[CAccessToken::getThreadToken](#getthreadtoken),但在從線程的訪問權杖`CAccessToken`初始化 之前設置類比級別。

[CAuto 還原類比類](../../atl/reference/cautorevertimpersonation-class.md)可用於透過將*bImpersonate*標誌設定為 TRUE 自動還原建立的模擬存取權杖。

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a>CAccessToken::P里維萊格檢查

呼叫此方法以確定物件中`CAccessToken`是否啟用了指定的許可權集。

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>參數

*必要權限*<br/>
指向[PRIVILEGE_SET](/windows/win32/api/winnt/ns-winnt-privilege_set)結構的指標。

*pb 結果*<br/>
指向方法集的值的指標,以指示`CAccessToken`物件中是否啟用了任何或所有指定的許可權。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

返回`PrivilegeCheck`時,`Attributes`如果 啟用了相應的許可權,則每個[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)結構的成員設置為SE_PRIVILEGE_USED_FOR_ACCESS。 此方法調用[特權檢查](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck)Win32 函數。

## <a name="caccesstokenrevert"></a><a name="revert"></a>CAccessToken::恢復

調用此方法以阻止線程使用類比權杖。

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>參數

*hThread*<br/>
句柄到線程以從類比還原。 如果*hThread*為 NULL,則假定當前線程。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

類比權杖的還原可以使用[CAuto還原類比類](../../atl/reference/cautorevertimpersonation-class.md)自動執行。

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a>CAccessToken::設定預設Dacl

呼叫此方法以設定`CAccessToken`物件的預設 DACL。

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>參數

*rDacl*<br/>
新的預設[CDacl 類](../../atl/reference/cdacl-class.md)資訊。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

默認 DACL 是 DACL,預設情況下,當使用此訪問權杖創建新物件時,它使用 DACL。

## <a name="caccesstokensetowner"></a><a name="setowner"></a>CAccessToken::SetOwner

調用此方法以設置`CAccessToken`物件的擁有者。

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
包含擁有者資訊的[CSid 類](../../atl/reference/csid-class.md)物件。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

擁有者是預設擁有者,用於在此訪問權杖生效時創建的新物件。

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a>CAccessToken::設定主要組

調用此方法以設置`CAccessToken`物件的主組。

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
包含主組資訊的[CSid 類](../../atl/reference/csid-class.md)物件。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

主組是此訪問權杖生效時創建的新物件的預設組。

## <a name="see-also"></a>另請參閱

[ATL 安全範例](../../overview/visual-cpp-samples.md)<br/>
[存取權杖](/windows/win32/SecAuthZ/access-tokens)<br/>
[類別概觀](../../atl/atl-class-overview.md)
