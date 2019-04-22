---
title: CTokenGroups 類別
ms.date: 11/04/2016
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
ms.openlocfilehash: 934d746dafafb39c2ffc3477c59c95914d270196
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772822"
---
# <a name="ctokengroups-class"></a>CTokenGroups 類別

這個類別是包裝函式`TOKEN_GROUPS`結構。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class CTokenGroups
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|建構函式。|
|[CTokenGroups::~CTokenGroups](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTokenGroups::Add](#add)|新增`CSid`或現有`TOKEN_GROUPS`結構`CTokenGroups`物件。|
|[CTokenGroups::Delete](#delete)|刪除`CSid`及其相關聯的屬性，從`CTokenGroups`物件。|
|[CTokenGroups::DeleteAll](#deleteall)|刪除所有`CSid`物件和其相關聯的屬性，從`CTokenGroups`物件。|
|[CTokenGroups::GetCount](#getcount)|傳回的數目`CSid`物件和相關聯的屬性中包含`CTokenGroups`物件。|
|[CTokenGroups::GetLength](#getlength)|傳回的大小`CTokenGroups`物件。|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|擷取的指標`TOKEN_GROUPS`結構。|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|擷取`CSid`物件和屬性屬於`CTokenGroups`物件。|
|[CTokenGroups::LookupSid](#lookupsid)|擷取相關聯的屬性`CSid`物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|轉型`CTokenGroups`物件的指標`TOKEN_GROUPS`結構。|
|[CTokenGroups::operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

[存取權杖](/windows/desktop/SecAuthZ/access-tokens)是說明處理序或執行緒的安全性內容，並配置給每位使用者登入 Windows 系統的物件。

`CTokenGroups`類別是包裝函式[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)結構，包含存取權杖中的群組安全性識別碼 (Sid) 相關資訊。

在 Windows 中的存取控制模型的簡介，請參閱 <<c0> [ 存取控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="requirements"></a>需求

**標頭：** atlsecurity.h

##  <a name="add"></a>  CTokenGroups::Add

新增`CSid`或現有`TOKEN_GROUPS`結構`CTokenGroups`物件。

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
A [CSid](../../atl/reference/csid-class.md)物件。

*dwAttributes*<br/>
相關聯的屬性`CSid`物件。

*rTokenGroups*<br/>
A [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)結構。

### <a name="remarks"></a>備註

這些方法會新增一或多個`CSid`物件和其相關聯的屬性，以`CTokenGroups`物件。

##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups

建構函式。

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
`CTokenGroups`物件或[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)結構，用來建構`CTokenGroups`物件。

### <a name="remarks"></a>備註

`CTokenGroups`物件可以選擇性地使用來建立`TOKEN_GROUPS`結構或先前定義`CTokenGroups`物件。

##  <a name="dtor"></a>  CTokenGroups:: ~ CTokenGroups

解構函式。

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>備註

解構函式會釋放所有配置的資源。

##  <a name="delete"></a>  CTokenGroups::Delete

刪除`CSid`及其相關聯的屬性，從`CTokenGroups`物件。

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>參數

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)的安全性識別碼 (SID) 和屬性應該將要移除的物件。

### <a name="return-value"></a>傳回值

傳回則為 true`CSid`已移除，false 否則。

##  <a name="deleteall"></a>  CTokenGroups::DeleteAll

刪除所有`CSid`物件和其相關聯的屬性，從`CTokenGroups`物件。

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>  CTokenGroups::GetCount

傳回的數目`CSid`中所包含的物件`CTokenGroups`。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回的數目[CSid](../../atl/reference/csid-class.md)物件和關聯的屬性中包含`CTokenGroups`物件。

##  <a name="getlength"></a>  CTokenGroups::GetLength

傳回的大小`CTokenGroup`物件。

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>備註

傳回的大小總計`CTokenGroup`物件，以位元組為單位。

##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS

擷取的指標`TOKEN_GROUPS`結構。

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>傳回值

擷取的指標[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)結構屬於`CTokenGroups`存取權杖的物件。

##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes

擷取`CSid`物件及 （選擇性） 的屬性屬於`CTokenGroups`物件。

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSids*<br/>
陣列的指標[CSid](../../atl/reference/csid-class.md)物件。

*pAttributes*<br/>
Dword 的陣列指標。 如果這個參數是省略，則為 NULL，不會擷取屬性。

### <a name="remarks"></a>備註

這個方法會列舉所有`CSid`中所包含的物件`CTokenGroups`物件，並將它們及 （選擇性） 的屬性旗標放入陣列物件。

##  <a name="lookupsid"></a>  CTokenGroups::LookupSid

擷取相關聯的屬性`CSid`物件。

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>參數

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)物件。

*pdwAttributes*<br/>
這將會接受 DWORD 指標`CSid`物件的屬性。 如果省略則為 NULL，將不會擷取屬性。

### <a name="return-value"></a>傳回值

傳回則為 true`CSid`找到，則為 false 否則。

### <a name="remarks"></a>備註

設定*pdwAttributes*到 NULL 提供一個方式來確認是否存在`CSid`而不需存取的屬性。 請注意，這個方法不應檢查存取權限。 應用程式應該改用[CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership)方法。

##  <a name="operator_eq"></a>  CTokenGroups::operator =

指派運算子。

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
`CTokenGroups`物件或[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)將指派給結構`CTokenGroups`物件。

### <a name="return-value"></a>傳回值

傳回已更新`CTokenGroups`物件。

##  <a name="operator_const_token_groups__star"></a>  CTokenGroups::operator const TOKEN_GROUPS *

將指標值轉換`TOKEN_GROUPS`結構。

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>備註

將指標值轉換[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups)結構。

## <a name="see-also"></a>另請參閱

[安全性範例](../../overview/visual-cpp-samples.md)<br/>
[CSid 類別](../../atl/reference/csid-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)
