---
title: CToken 群組類別
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
ms.openlocfilehash: 1e9d21c59eb5efabf036fbc938a40de2c4b7a0b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330556"
---
# <a name="ctokengroups-class"></a>CToken 群組類別

此類是結構的`TOKEN_GROUPS`包裝器。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CTokenGroups
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CToken 群組:CToken 群組](#ctokengroups)|建構函式。|
|[CToken 群組:*CToken 群組](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CToken 群組::新增](#add)|將`CSid`或現有`TOKEN_GROUPS`結構添加到`CTokenGroups`物件。|
|[CToken組::Delete](#delete)|從`CTokenGroups`物件中`CSid`刪除 a 及其關聯的屬性。|
|[CToken組::DeleteAll](#deleteall)|從`CTokenGroups`物件中`CSid`刪除 所有物件及其關聯屬性。|
|[CToken 群組:取得計數](#getcount)|傳回物件包含的`CSid`物件與關聯屬性的`CTokenGroups`數量 。|
|[CToken 群組:取得長度](#getlength)|返回`CTokenGroups`物件的大小。|
|[CToken 組::GetPTOKEN_GROUPS](#getptoken_groups)|檢索指向結構的`TOKEN_GROUPS`指標。|
|[Ctoken 群組::取得 Sids 和屬性](#getsidsandattributes)|檢索屬於`CSid``CTokenGroups`物件的物件和屬性。|
|[CToken 群組::尋找Sid](#lookupsid)|檢索與`CSid`對象關聯的屬性。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CToken組::操作員TOKEN_GROUPS |](#operator_const_token_groups__star)|將`CTokenGroups`對象強制轉換為指向結構`TOKEN_GROUPS`的指標。|
|[CToken組::運算符 |](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

[訪問權杖](/windows/win32/SecAuthZ/access-tokens)是描述進程或線程的安全上下文並分配給登錄到 Windows 系統的每個使用者的物件。

類`CTokenGroups`是[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)結構的包裝器,包含有關訪問權杖中的組安全標識符 (SID) 的資訊。

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="ctokengroupsadd"></a><a name="add"></a>CToken 群組::新增

將`CSid`或現有`TOKEN_GROUPS`結構添加到`CTokenGroups`物件。

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)物件。

*dwAttributes*<br/>
要與`CSid`物件關聯的屬性。

*rToken群組*<br/>
[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)結構。

### <a name="remarks"></a>備註

這些方法向`CTokenGroups`物件添加一個或`CSid`多個 物件及其關聯屬性。

## <a name="ctokengroupsctokengroups"></a><a name="ctokengroups"></a>CToken 群組:CToken 群組

建構函式。

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`CTokenGroups`用來[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)構造`CTokenGroups`物件的物件或TOKEN_GROUPS結構。

### <a name="remarks"></a>備註

可以選擇`CTokenGroups``TOKEN_GROUPS`使用結構或以前`CTokenGroups`定義的物件創建該物件。

## <a name="ctokengroupsctokengroups"></a><a name="dtor"></a>CToken 群組:*CToken 群組

解構函式。

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>備註

析構函數釋放所有分配的資源。

## <a name="ctokengroupsdelete"></a><a name="delete"></a>CToken組::Delete

從`CTokenGroups`物件中`CSid`刪除 a 及其關聯的屬性。

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>參數

*rSid*<br/>
應為其刪除安全識別碼 (SID) 和屬性的[CSid](../../atl/reference/csid-class.md)物件。

### <a name="return-value"></a>傳回值

如果刪除,`CSid`則返回 true,否則為 false。

## <a name="ctokengroupsdeleteall"></a><a name="deleteall"></a>CToken組::DeleteAll

從`CTokenGroups`物件中`CSid`刪除 所有物件及其關聯屬性。

```
void DeleteAll() throw();
```

## <a name="ctokengroupsgetcount"></a><a name="getcount"></a>CToken 群組:取得計數

返回 中包含`CSid``CTokenGroups`的 物件數。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回物件包含的[CSid](../../atl/reference/csid-class.md)物件與關聯屬性`CTokenGroups`的數量 。

## <a name="ctokengroupsgetlength"></a><a name="getlength"></a>CToken 群組:取得長度

返回`CTokenGroup`物件的大小。

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>備註

返回`CTokenGroup`物件的總大小(以位元組為單位)。

## <a name="ctokengroupsgetptoken_groups"></a><a name="getptoken_groups"></a>CToken 組::GetPTOKEN_GROUPS

檢索指向結構的`TOKEN_GROUPS`指標。

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>傳回值

檢索指向屬於訪問權杖物件的[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)結構的`CTokenGroups`指標。

## <a name="ctokengroupsgetsidsandattributes"></a><a name="getsidsandattributes"></a>Ctoken 群組::取得 Sids 和屬性

檢索`CSid`物件和(可選)`CTokenGroups`屬於 該物件的屬性。

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSids*<br/>
指向[CSid](../../atl/reference/csid-class.md)物件的陣列。

*pAttributes*<br/>
指向 DORD 陣列的指標。 如果省略此參數或 NULL,則不檢索屬性。

### <a name="remarks"></a>備註

此方法將枚舉`CSid``CTokenGroups`物件中包含的所有物件並將其放置,並(有選擇地)將屬性標誌放入陣列物件中。

## <a name="ctokengroupslookupsid"></a><a name="lookupsid"></a>CToken 群組::尋找Sid

檢索與`CSid`對象關聯的屬性。

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>參數

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)物件。

*pdwAttributes*<br/>
指向將接受`CSid`物件的屬性的 DWORD 的指標。 如果省略或 NULL,將不會檢索該屬性。

### <a name="return-value"></a>傳回值

如果找到`CSid`, 則傳回 true,否則為 false。

### <a name="remarks"></a>備註

將*pdwAttributes*設定為 NULL`CSid`提供了一種 在不訪問屬性的情況下確認 是否存在的方法。 請注意,此方法不應用於檢查訪問許可權。 相反,應用程式應使用[CAccessToken::檢查權杖成員資格](../../atl/reference/caccesstoken-class.md#checktokenmembership)方法。

## <a name="ctokengroupsoperator-"></a><a name="operator_eq"></a>CToken組::運算符 |

指派運算子。

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`CTokenGroups`分配給`CTokenGroups`物件的物件或[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)結構。

### <a name="return-value"></a>傳回值

返回更新`CTokenGroups`的物件。

## <a name="ctokengroupsoperator-const-token_groups-"></a><a name="operator_const_token_groups__star"></a>CToken組::操作員TOKEN_GROUPS |

將值投射到指向結構的`TOKEN_GROUPS`指標。

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>備註

將值投射到指向[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)結構的指標。

## <a name="see-also"></a>另請參閱

[安全範例](../../overview/visual-cpp-samples.md)<br/>
[CSid 類別](../../atl/reference/csid-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全全域功能](../../atl/reference/security-global-functions.md)
