---
title: CTokenPrivileges 類別
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
ms.openlocfilehash: 5f8379d20d8c8d525cd645e1d4aa0c751e16f531
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915529"
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges 類別

這個類別是`TOKEN_PRIVILEGES`結構的包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CTokenPrivileges
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|建構函式。|
|[CTokenPrivileges:: ~ CTokenPrivileges](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTokenPrivileges::Add](#add)|將一個或多個許可權新增`CTokenPrivileges`至物件。|
|[CTokenPrivileges::Delete](#delete)|從`CTokenPrivileges`物件中刪除許可權。|
|[CTokenPrivileges::DeleteAll](#deleteall)|刪除物件的`CTokenPrivileges`擁有權限。|
|[CTokenPrivileges::GetCount](#getcount)|傳回`CTokenPrivileges`物件中的許可權專案數目。|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|抓取`CTokenPrivileges`物件中包含之許可權的顯示名稱。|
|[CTokenPrivileges::GetLength](#getlength)|傳回保留`TOKEN_PRIVILEGES` `CTokenPrivileges`物件所代表之結構所需的緩衝區大小 (以位元組為單位)。|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|從`CTokenPrivileges`物件中抓取本機唯一識別碼 (luid) 和屬性旗標。|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|從`CTokenPrivileges`物件中抓取許可權名稱和屬性旗標。|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|傳回結構的`TOKEN_PRIVILEGES`指標。|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|抓取與指定的許可權名稱相關聯的屬性。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CTokenPrivileges:: operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|將值轉換成結構的`TOKEN_PRIVILEGES`指標。|
|[CTokenPrivileges:: operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

[存取權杖](/windows/desktop/SecAuthZ/access-tokens)是一種物件, 可描述處理常式或執行緒的安全性內容, 並配置給每位登入 Windows 系統的使用者。

存取權杖是用來描述授與給每個使用者的各種安全性許可權。 許可權包含64位數位, 稱為本機唯一識別碼 ( [LUID](/windows/desktop/api/winnt/ns-winnt-luid)) 和描述元字串。

類別是 [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) 結構的包裝函式, 其中包含0個或更多的許可權。`CTokenPrivileges` 您可以使用提供的類別方法來新增、刪除或查詢許可權。

如需 Windows 中的存取控制模型簡介, 請參閱 Windows SDK 中的[存取控制](/windows/desktop/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標頭:** atlsecurity。h

##  <a name="add"></a>CTokenPrivileges:: Add

將一或多個許可權新增`CTokenPrivileges`至存取權杖物件。

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>參數

*pszPrivilege*<br/>
以 null 結束的字串指標, 指定許可權的名稱, 如 WINNT 中所定義。H 標頭檔。

*bEnable*<br/>
若為 true, 則表示已啟用許可權。 如果為 false, 則表示許可權已停用。

*rPrivileges*<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges)結構的參考。 許可權和屬性會從此結構複製並新增至`CTokenPrivileges`物件。

### <a name="return-value"></a>傳回值

如果成功加入許可權, 則此方法的第一個形式會傳回 true, 否則傳回 false。

##  <a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges

建構函式。

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`CTokenPrivileges`指派給新物件的物件。

*rPrivileges*<br/>
要指派給新`CTokenPrivileges`物件的 [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) 結構。

### <a name="remarks"></a>備註

您`CTokenPrivileges`可以選擇性地`TOKEN_PRIVILEGES`使用結構或先前定義`CTokenPrivileges`的物件來建立物件。

##  <a name="dtor"></a>CTokenPrivileges:: ~ CTokenPrivileges

解構函式。

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>備註

此析構函式會釋放所有配置的資源。

##  <a name="delete"></a>CTokenPrivileges::D 刪除

從`CTokenPrivileges`存取權杖物件中刪除許可權。

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>參數

*pszPrivilege*<br/>
以 null 結束的字串指標, 指定許可權的名稱, 如 WINNT 中所定義。H 標頭檔。 例如, 此參數可以指定常數 SE_SECURITY_NAME 或其對應的字串 "SeSecurityPrivilege"。

### <a name="return-value"></a>傳回值

如果已成功刪除許可權, 則傳回 true, 否則傳回 false。

### <a name="remarks"></a>備註

這個方法很適合用來建立受限制的權杖。

##  <a name="deleteall"></a>  CTokenPrivileges::DeleteAll

刪除存取權杖物件中`CTokenPrivileges`的擁有權限。

```
void DeleteAll() throw();
```

### <a name="remarks"></a>備註

刪除存取權杖物件中包含`CTokenPrivileges`的擁有權限。

##  <a name="getdisplaynames"></a>  CTokenPrivileges::GetDisplayNames

抓取`CTokenPrivileges`存取權杖物件中所包含之許可權的顯示名稱。

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>參數

*pDisplayNames*<br/>
`CString` 物件陣列的指標。 `CNames`定義為 typedef: `CTokenPrivileges::CAtlArray<CString>`。

### <a name="remarks"></a>備註

參數`pDisplayNames`是物件陣列的`CString`指標, 會接收與`CTokenPrivileges`物件中包含之許可權對應的顯示名稱。 這個方法只會針對 WINNT 的 [定義的許可權] 區段中所指定的許可權來抓取顯示名稱。H.

這個方法會抓取可顯示的名稱: 例如, 如果屬性名稱是 SE_REMOTE_SHUTDOWN_NAME, 可顯示的名稱是「強制關閉遠端系統」。 若要取得系統名稱, 請使用[CTokenPrivileges:: GetNamesAndAttributes](#getnamesandattributes)。

##  <a name="getcount"></a>  CTokenPrivileges::GetCount

傳回`CTokenPrivileges`物件中的許可權專案數目。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回`CTokenPrivileges`物件中包含的許可權數目。

##  <a name="getlength"></a>CTokenPrivileges:: GetLength

傳回`CTokenPrivileges`物件的長度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>傳回值

傳回保留`TOKEN_PRIVILEGES` `CTokenPrivileges`物件所代表之結構所需的位元組數目, 包括其中包含的擁有權限專案。

##  <a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes

從`CTokenPrivileges`物件中抓取本機唯一識別碼 (luid) 和屬性旗標。

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pPrivileges*<br/>
[LUID](/windows/desktop/api/winnt/ns-winnt-luid)物件陣列的指標。 `CLUIDArray`這是定義為`CAtlArray<LUID> CLUIDArray`的 typedef。

*pAttributes*<br/>
DWORD 物件陣列的指標。 如果省略此參數或為 Null, 則不會抓取屬性。 `CAttributes`這是定義為`CAtlArray <DWORD> CAttributes`的 typedef。

### <a name="remarks"></a>備註

這個方法會列舉`CTokenPrivileges`存取權杖物件中包含的擁有權限, 並將個別 luid 和 (選擇性) 的屬性旗標放入陣列物件中。

##  <a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes

從`CTokenPrivileges`物件中抓取名稱和屬性旗標。

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pNames*<br/>
物件陣列的`CString`指標。 `CNames`這是定義為`CAtlArray <CString> CNames`的 typedef。

*pAttributes*<br/>
DWORD 物件陣列的指標。 如果省略此參數或為 Null, 則不會抓取屬性。 `CAttributes`這是定義為`CAtlArray <DWORD> CAttributes`的 typedef。

### <a name="remarks"></a>備註

這個方法會列舉`CTokenPrivileges`物件中包含的擁有權限, 並將名稱和 (選擇性) 屬性旗標放入陣列物件中。

這個方法會抓取屬性名稱, 而不是可顯示的名稱: 例如, 如果屬性名稱是 SE_REMOTE_SHUTDOWN_NAME, 則系統名稱會是 "SeRemoteShutdownPrivilege"。 若要取得可顯示的名稱, 請使用[CTokenPrivileges:: GetDisplayNames](#getdisplaynames)方法。

##  <a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES

傳回結構的`TOKEN_PRIVILEGES`指標。

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>傳回值

傳回[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges)結構的指標。

##  <a name="lookupprivilege"></a>  CTokenPrivileges::LookupPrivilege

抓取與指定的許可權名稱相關聯的屬性。

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pszPrivilege*<br/>
以 null 結束的字串指標, 指定許可權的名稱, 如 WINNT 中所定義。H 標頭檔。 例如, 此參數可以指定常數 SE_SECURITY_NAME 或其對應的字串 "SeSecurityPrivilege"。

*pdwAttributes*<br/>
接收屬性之變數的指標。

### <a name="return-value"></a>傳回值

如果成功抓取屬性, 則傳回 true, 否則傳回 false。

##  <a name="operator_eq"></a>CTokenPrivileges:: operator =

指派運算子。

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rPrivileges*<br/>
要指派給`CTokenPrivileges`物件的 [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges) 結構。

*rhs*<br/>
要`CTokenPrivileges`指派給物件的物件。

### <a name="return-value"></a>傳回值

傳回已更新`CTokenPrivileges`的物件。

##  <a name="operator_const_token_privileges__star"></a>CTokenPrivileges:: operator const TOKEN_PRIVILEGES\*

將值轉換成結構的`TOKEN_PRIVILEGES`指標。

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>備註

將值轉換成[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges)結構的指標。

## <a name="see-also"></a>另請參閱

[安全性範例](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-token_privileges)<br/>
[LUID](/windows/desktop/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-luid_and_attributes)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)
