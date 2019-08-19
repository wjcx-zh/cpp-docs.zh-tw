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
ms.openlocfilehash: 4e5d06ca01201bf415afedbe6f6e5bca096f68fa
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915583"
---
# <a name="ctokengroups-class"></a>CTokenGroups 類別

這個類別是`TOKEN_GROUPS`結構的包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CTokenGroups
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|建構函式。|
|[CTokenGroups::~CTokenGroups](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CTokenGroups::Add](#add)|將或現有`TOKEN_GROUPS`結構加入至`CTokenGroups`物件。 `CSid`|
|[CTokenGroups::Delete](#delete)|從物件中刪除和其相關聯的屬性。 `CSid` `CTokenGroups`|
|[CTokenGroups::DeleteAll](#deleteall)|從物件中刪除所有`CSid`物件及其相關聯的屬性。 `CTokenGroups`|
|[CTokenGroups::GetCount](#getcount)|傳回物件`CSid` `CTokenGroups`中包含的物件數目和相關聯的屬性。|
|[CTokenGroups::GetLength](#getlength)|傳回`CTokenGroups`物件的大小。|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|抓取`TOKEN_GROUPS`結構的指標。|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|抓取屬於`CSid` `CTokenGroups`物件的物件和屬性。|
|[CTokenGroups::LookupSid](#lookupsid)|抓取與`CSid`物件相關聯的屬性。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CTokenGroups:: operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|將物件轉換成`TOKEN_GROUPS`結構的指標。 `CTokenGroups`|
|[CTokenGroups:: operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

[存取權杖](/windows/desktop/SecAuthZ/access-tokens)是一種物件, 可描述處理常式或執行緒的安全性內容, 並配置給每位登入 Windows 系統的使用者。

類別是 [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) 結構的包裝函式, 其中包含存取權杖中的群組安全識別碼 (sid) 的相關資訊。`CTokenGroups`

如需 Windows 中的存取控制模型簡介, 請參閱 Windows SDK 中的[存取控制](/windows/desktop/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標頭:** atlsecurity。h

##  <a name="add"></a>CTokenGroups:: Add

將或現有`TOKEN_GROUPS`結構加入至`CTokenGroups`物件。 `CSid`

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)物件。

*dwAttributes*<br/>
要與`CSid`物件產生關聯的屬性。

*rTokenGroups*<br/>
[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups)結構。

### <a name="remarks"></a>備註

這些方法會將一或`CSid`多個物件及其相關聯的`CTokenGroups`屬性加入至物件。

##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups

建構函式。

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
用`CTokenGroups`來建立 `CTokenGroups`物件的物件或 [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) 結構。

### <a name="remarks"></a>備註

您`CTokenGroups`可以選擇性地`TOKEN_GROUPS`使用結構或先前定義`CTokenGroups`的物件來建立物件。

##  <a name="dtor"></a>CTokenGroups:: ~ CTokenGroups

解構函式。

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>備註

此析構函式會釋放所有配置的資源。

##  <a name="delete"></a>  CTokenGroups::Delete

從物件中刪除和其相關聯的屬性。 `CSid` `CTokenGroups`

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>參數

*rSid*<br/>
應移除安全識別碼 (SID) 和屬性的[CSid](../../atl/reference/csid-class.md)物件。

### <a name="return-value"></a>傳回值

如果`CSid`已移除, 則傳回 true, 否則傳回 false。

##  <a name="deleteall"></a>  CTokenGroups::DeleteAll

從物件中刪除所有`CSid`物件及其相關聯的屬性。 `CTokenGroups`

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>  CTokenGroups::GetCount

傳回中`CSid` `CTokenGroups`所包含的物件數目。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回`CTokenGroups`物件中包含的[CSid](../../atl/reference/csid-class.md)物件和其相關聯屬性的數目。

##  <a name="getlength"></a>  CTokenGroups::GetLength

傳回`CTokenGroup`物件的大小。

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>備註

傳回`CTokenGroup`物件的大小總計 (以位元組為單位)。

##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS

抓取`TOKEN_GROUPS`結構的指標。

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>傳回值

抓取屬於`CTokenGroups`存取權杖物件之[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups)結構的指標。

##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes

抓取物件和 (選擇性) 屬於`CTokenGroups`物件的屬性。 `CSid`

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSids*<br/>
[CSid](../../atl/reference/csid-class.md)物件陣列的指標。

*pAttributes*<br/>
Dword 陣列的指標。 如果省略此參數或為 Null, 則不會抓取屬性。

### <a name="remarks"></a>備註

這個方法會列舉`CSid` `CTokenGroups`物件中包含的所有物件, 並將其和 (選擇性) 屬性旗標放入陣列物件中。

##  <a name="lookupsid"></a>  CTokenGroups::LookupSid

抓取與`CSid`物件相關聯的屬性。

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>參數

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)物件。

*pdwAttributes*<br/>
DWORD 的指標, 它會接受`CSid`物件的屬性。 如果省略或為 Null, 則不會抓取屬性。

### <a name="return-value"></a>傳回值

如果`CSid`找到, 則傳回 true, 否則傳回 false。

### <a name="remarks"></a>備註

將*pdwAttributes*設定為 Null 提供了一種方法來確認是否`CSid`存在, 而不需要存取屬性。 請注意, 這個方法不應該用來檢查存取權限。 應用程式應改為使用[CAccessToken:: CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership)方法。

##  <a name="operator_eq"></a>CTokenGroups:: operator =

指派運算子。

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要指派`CTokenGroups`給 物件的物件或[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups)`CTokenGroups`結構。

### <a name="return-value"></a>傳回值

傳回已更新`CTokenGroups`的物件。

##  <a name="operator_const_token_groups__star"></a>CTokenGroups:: operator const TOKEN_GROUPS *

將值轉換成結構的`TOKEN_GROUPS`指標。

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>備註

將值轉換成[TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups)結構的指標。

## <a name="see-also"></a>另請參閱

[安全性範例](../../overview/visual-cpp-samples.md)<br/>
[CSid 類別](../../atl/reference/csid-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)
