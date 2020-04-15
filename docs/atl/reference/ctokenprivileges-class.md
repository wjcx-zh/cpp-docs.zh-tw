---
title: CToken 特權類
ms.date: 11/04/2016
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
ms.openlocfilehash: ceb9aeca6b99e7fc9d08625e11cbdb182fb3dc9e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330536"
---
# <a name="ctokenprivileges-class"></a>CToken 特權類

此類是結構的`TOKEN_PRIVILEGES`包裝器。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CTokenPrivileges
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CToken 特權::CToken 特權](#ctokenprivileges)|建構函式。|
|[CToken 特權::*CToken 特權](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CToken 特權::添加](#add)|向`CTokenPrivileges`物件添加一個或多個許可權。|
|[CToken 特權::Delete](#delete)|從`CTokenPrivileges`物件中刪除許可權。|
|[CToken 特權::DeleteAll](#deleteall)|從`CTokenPrivileges`物件中刪除所有許可權。|
|[CToken 特權::獲取計數](#getcount)|返回`CTokenPrivileges`物件中的許可權條目數。|
|[CToken 特權::取得顯示名稱](#getdisplaynames)|檢索物件中包含的特權的`CTokenPrivileges`顯示名稱。|
|[CToken 特權:取得長度](#getlength)|返回保存`TOKEN_PRIVILEGES``CTokenPrivileges`物件表示的結構所需的緩衝區大小(以位元組為單位)。|
|[CToken 特權::取得 Luids 和屬性](#getluidsandattributes)|從`CTokenPrivileges`物件檢索本地唯一標識符 (LUID) 和屬性標誌。|
|[CToken 權限:取得名稱和屬性](#getnamesandattributes)|從`CTokenPrivileges`物件檢索特權名稱和屬性標誌。|
|[CToken 特權::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|返回指向結構的`TOKEN_PRIVILEGES`指標。|
|[CToken 特權::查找特權](#lookupprivilege)|檢索與給定許可權名稱關聯的屬性。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CToken 特權::運算符 TOKEN_PRIVILEGES |](#operator_const_token_privileges__star)|將值投射到指向結構的`TOKEN_PRIVILEGES`指標。|
|[CToken 特權::運算符 |](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

[訪問權杖](/windows/win32/SecAuthZ/access-tokens)是描述進程或線程的安全上下文並分配給登錄到 Windows 系統的每個使用者的物件。

訪問權杖用於描述授予每個使用者的各種安全特權。 特權由稱為本地唯一標識符[(LUID](/windows/win32/api/winnt/ns-winnt-luid)) 的 64 位元數位和描述符字串組成。

類`CTokenPrivileges`是[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)結構的包裝器,包含0或更多許可權。 可以使用提供的類方法添加、刪除或查詢許可權。

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="ctokenprivilegesadd"></a><a name="add"></a>CToken 特權::添加

向`CTokenPrivileges`訪問權杖物件添加一個或多個許可權。

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>參數

*psz特權*<br/>
指向 null 連接端的字串的指標,該字串指定在 WINNT 中定義的特權的名稱。H 頭檔。

*b 啟用*<br/>
如果為 true,則啟用該許可權。 如果為 false,則禁用該特權。

*r特權*<br/>
對[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)結構的引用。 特權和屬性從此結構複製並添加到`CTokenPrivileges`物件中。

### <a name="return-value"></a>傳回值

如果成功添加許可權,此方法的第一種形式將返回 true,否則為 false。

## <a name="ctokenprivilegesctokenprivileges"></a><a name="ctokenprivileges"></a>CToken 特權::CToken 特權

建構函式。

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`CTokenPrivileges`分配給新物件的物件。

*r特權*<br/>
要[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)分配給新`CTokenPrivileges`物件的TOKEN_PRIVILEGES結構。

### <a name="remarks"></a>備註

可以選擇`CTokenPrivileges``TOKEN_PRIVILEGES`使用結構或以前`CTokenPrivileges`定義的物件創建該物件。

## <a name="ctokenprivilegesctokenprivileges"></a><a name="dtor"></a>CToken 特權::*CToken 特權

解構函式。

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>備註

析構函數釋放所有分配的資源。

## <a name="ctokenprivilegesdelete"></a><a name="delete"></a>CToken 特權::Delete

從`CTokenPrivileges`存取權限中刪除許可權。

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>參數

*psz特權*<br/>
指向 null 連接端的字串的指標,該字串指定在 WINNT 中定義的特權的名稱。H 頭檔。 例如,此參數可以指定常量SE_SECURITY_NAME或其相應的字串"SeSecurity特權"

### <a name="return-value"></a>傳回值

如果成功刪除許可權,則返回 true,否則為 false。

### <a name="remarks"></a>備註

此方法可用作創建受限權杖的工具。

## <a name="ctokenprivilegesdeleteall"></a><a name="deleteall"></a>CToken 特權::DeleteAll

從`CTokenPrivileges`訪問權杖物件中刪除所有許可權。

```
void DeleteAll() throw();
```

### <a name="remarks"></a>備註

刪除`CTokenPrivileges`存取權限中包含的所有許可權。

## <a name="ctokenprivilegesgetdisplaynames"></a><a name="getdisplaynames"></a>CToken 特權::取得顯示名稱

檢索訪問權杖物件中包含的特權的`CTokenPrivileges`顯示名稱。

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>參數

*p 顯示名稱*<br/>
`CString` 物件陣列的指標。 `CNames`定義為類型def: `CTokenPrivileges::CAtlArray<CString>`。

### <a name="remarks"></a>備註

參數`pDisplayNames`是指向物件數組`CString`的指標,該陣列將接收與物件中包含的特權對應的`CTokenPrivileges`顯示名稱。 此方法僅檢索 WINNT"定義許可權"部分中指定的許可權的顯示名稱。H。

此方法檢索可顯示的名稱:例如,如果屬性名稱SE_REMOTE_SHUTDOWN_NAME,則可顯示的名稱為「從遠端系統強制關閉」。 要取得系統名稱,請使用[Ctoken 特權::取得名稱和屬性](#getnamesandattributes)。

## <a name="ctokenprivilegesgetcount"></a><a name="getcount"></a>CToken 特權::獲取計數

返回`CTokenPrivileges`物件中的許可權條目數。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>傳回值

返回`CTokenPrivileges`物件中包含的許可權數。

## <a name="ctokenprivilegesgetlength"></a><a name="getlength"></a>CToken 特權:取得長度

返回`CTokenPrivileges`物件的長度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>傳回值

返回保存`TOKEN_PRIVILEGES``CTokenPrivileges`由物件表示的結構所需的位元組數,包括它包含的所有特權條目。

## <a name="ctokenprivilegesgetluidsandattributes"></a><a name="getluidsandattributes"></a>CToken 特權::取得 Luids 和屬性

從`CTokenPrivileges`物件檢索本地唯一標識符 (LUID) 和屬性標誌。

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*p權限*<br/>
指向[LUID](/windows/win32/api/winnt/ns-winnt-luid)物件的陣列。 `CLUIDArray`是定義為`CAtlArray<LUID> CLUIDArray`的類型def。

*pAttributes*<br/>
指向 DWORD 物件的陣列。 如果省略此參數或 NULL,則不檢索屬性。 `CAttributes`是定義為`CAtlArray <DWORD> CAttributes`的類型def。

### <a name="remarks"></a>備註

此方法將枚舉`CTokenPrivileges`訪問權杖物件中包含的所有許可權,並將單獨的 LUID 和(可選)屬性標誌放入陣列中。

## <a name="ctokenprivilegesgetnamesandattributes"></a><a name="getnamesandattributes"></a>CToken 權限:取得名稱和屬性

從`CTokenPrivileges`物件檢索名稱和屬性標誌。

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*p 名稱*<br/>
指向物件數組的`CString`指標。 `CNames`是定義為`CAtlArray <CString> CNames`的類型def。

*pAttributes*<br/>
指向 DWORD 物件的陣列。 如果省略此參數或 NULL,則不檢索屬性。 `CAttributes`是定義為`CAtlArray <DWORD> CAttributes`的類型def。

### <a name="remarks"></a>備註

此方法將枚舉`CTokenPrivileges`物件中包含的所有許可權,將名稱和(可選)屬性標誌放入陣列物件中。

此方法檢索屬性名稱,而不是可顯示的名稱:例如,如果屬性名稱SE_REMOTE_SHUTDOWN_NAME,則系統名稱為"SeRemote 關閉許可權"。 要取得可顯示名稱,請使用方法[CToken 特權::取得顯示名稱](#getdisplaynames)。

## <a name="ctokenprivilegesgetptoken_privileges"></a><a name="getptoken_privileges"></a>CToken 特權::GetPTOKEN_PRIVILEGES

返回指向結構的`TOKEN_PRIVILEGES`指標。

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>傳回值

返回指向[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)結構的指標。

## <a name="ctokenprivilegeslookupprivilege"></a><a name="lookupprivilege"></a>CToken 特權::查找特權

檢索與給定許可權名稱關聯的屬性。

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*psz特權*<br/>
指向 null 連接端的字串的指標,該字串指定在 WINNT 中定義的特權的名稱。H 頭檔。 例如,此參數可以指定常量SE_SECURITY_NAME或其相應的字串"SeSecurity特權"

*pdwAttributes*<br/>
指向接收屬性的變數的指標。

### <a name="return-value"></a>傳回值

如果成功檢索屬性,則返回 true,否則為 false。

## <a name="ctokenprivilegesoperator-"></a><a name="operator_eq"></a>CToken 特權::運算符 |

指派運算子。

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>參數

*r特權*<br/>
要[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)分配給`CTokenPrivileges`物件的TOKEN_PRIVILEGES結構。

*rhs*<br/>
要`CTokenPrivileges`分配給物件的物件。

### <a name="return-value"></a>傳回值

返回更新`CTokenPrivileges`的物件。

## <a name="ctokenprivilegesoperator-const-token_privileges-"></a><a name="operator_const_token_privileges__star"></a>CToken 特權::運算符 TOKEN_PRIVILEGES\*

將值投射到指向結構的`TOKEN_PRIVILEGES`指標。

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>備註

將值投射到指向[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)結構的指標。

## <a name="see-also"></a>另請參閱

[安全範例](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)<br/>
[盧ID](/windows/win32/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全全域功能](../../atl/reference/security-global-functions.md)
