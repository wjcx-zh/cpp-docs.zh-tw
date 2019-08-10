---
title: CAcl 類別
ms.date: 11/04/2016
f1_keywords:
- CAcl
- ATLSECURITY/ATL::CAcl
- ATLSECURITY/ATL::CAcl::CAccessMaskArray
- ATLSECURITY/ATL::CAcl::CAceFlagArray
- ATLSECURITY/ATL::CAcl::CAceTypeArray
- ATLSECURITY/ATL::CAcl::CAcl
- ATLSECURITY/ATL::CAcl::GetAceCount
- ATLSECURITY/ATL::CAcl::GetAclEntries
- ATLSECURITY/ATL::CAcl::GetAclEntry
- ATLSECURITY/ATL::CAcl::GetLength
- ATLSECURITY/ATL::CAcl::GetPACL
- ATLSECURITY/ATL::CAcl::IsEmpty
- ATLSECURITY/ATL::CAcl::IsNull
- ATLSECURITY/ATL::CAcl::RemoveAce
- ATLSECURITY/ATL::CAcl::RemoveAces
- ATLSECURITY/ATL::CAcl::SetEmpty
- ATLSECURITY/ATL::CAcl::SetNull
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
ms.openlocfilehash: ba791ddc46fd59a470943bb30f415da01966dc61
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915895"
---
# <a name="cacl-class"></a>CAcl 類別

這個類別是 (存取控制清單`ACL` ) 結構的包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAcl
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|ACCESS_MASKs 的陣列。|
|[CAcl::CAceFlagArray](#caceflagarray)|位元組陣列。|
|[CAcl::CAceTypeArray](#cacetypearray)|位元組陣列。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|建構函式。|
|[CAcl:: ~ CAcl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|傳回存取控制專案 (ACE) 物件的數目。|
|[CAcl::GetAclEntries](#getaclentries)|從`CAcl`物件中抓取存取控制清單 (ACL) 專案。|
|[CAcl::GetAclEntry](#getaclentry)|抓取`CAcl`物件中某個專案的所有相關資訊。|
|[CAcl::GetLength](#getlength)|傳回 ACL 的長度。|
|[CAcl::GetPACL](#getpacl)|傳回 PACL (ACL 的指標)。|
|[CAcl::IsEmpty](#isempty)|測試專案的物件。 `CAcl`|
|[CAcl::IsNull](#isnull)|傳回`CAcl`物件的狀態。|
|[CAcl::RemoveAce](#removeace)|從`CAcl`物件中移除特定的 ACE (存取控制專案)。|
|[CAcl::RemoveAces](#removeaces)|從`CAcl`適用于指定`CSid`的, 移除所有的 ace (存取控制專案)。|
|[CAcl::SetEmpty](#setempty)|將`CAcl`物件標示為空白。|
|[CAcl::SetNull](#setnull)|將`CAcl`物件標記為 Null。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAcl:: operator const ACL *](#operator_const_acl__star)|將物件轉換成`ACL`結構。 `CAcl`|
|[CAcl:: operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

`ACL`結構是 ACL (存取控制清單) 的標頭。 ACL 包含零個或多個[ace](/windows/desktop/SecAuthZ/access-control-entries) (存取控制專案) 的連續清單。 ACL 中的個別 Ace 會從0編號到*n-1*, 其中*n*是 acl 中的 ace 數目。 編輯 ACL 時, 應用程式會依其索引參考 ACL 中的存取控制專案 (ACE)。

有兩種 ACL 類型:

- 自

- 系統

任意 ACL 是由物件的擁有者, 或授與物件之 WRITE_DAC 存取權的任何人所控制。 它會指定特定使用者和群組對物件的存取權。 例如, 檔案的擁有者可以使用任意的 ACL 來控制哪些使用者和群組可以和無法存取該檔案。

物件也可以有與其相關聯的系統層級安全性資訊, 其形式為系統管理員所控制的系統 ACL。 系統 ACL 可以讓系統管理員在嘗試取得物件的存取權時, 進行審核。

如需詳細資訊, 請參閱 Windows SDK 中的[ACL](/windows/desktop/SecAuthZ/access-control-lists)討論。

如需 Windows 中的存取控制模型簡介, 請參閱 Windows SDK 中的[存取控制](/windows/desktop/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標頭:** atlsecurity。h

##  <a name="caccessmaskarray"></a>CAcl::CAccessMaskArray

ACCESS_MASK 物件的陣列。

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>備註

這個 typedef 會指定可用來儲存存取控制專案 (Ace) 中所使用之存取權限的陣列類型。

##  <a name="caceflagarray"></a>CAcl::CAceFlagArray

位元組陣列。

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>備註

這個 typedef 會指定用來定義存取控制專案 (ACE) 類型特定控制項旗標的陣列類型。 如需可能旗標的完整清單, 請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-ace_header)定義。

##  <a name="cacetypearray"></a>  CAcl::CAceTypeArray

位元組陣列。

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>備註

這個 typedef 會指定用來定義存取控制專案 (ACE) 物件本質的陣列類型, 例如 ACCESS_ALLOWED_ACE_TYPE 或 ACCESS_DENIED_ACE_TYPE。 如需可能類型的完整清單, 請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-ace_header)定義。

##  <a name="cacl"></a>  CAcl::CAcl

建構函式。

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
現有的 `CAcl` 物件。

### <a name="remarks"></a>備註

可以`CAcl`選擇性地使用現有`CAcl`的物件建立物件。

##  <a name="dtor"></a>CAcl:: ~ CAcl

解構函式。

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>備註

此析構函式會釋放物件所取得的任何資源。

##  <a name="getacecount"></a>  CAcl::GetAceCount

傳回存取控制專案 (ACE) 物件的數目。

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>傳回值

傳回`CAcl`物件中的 ACE 專案數目。

##  <a name="getaclentries"></a>CAcl::GetAclEntries

從`CAcl`物件中抓取存取控制清單 (ACL) 專案。

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSids*<br/>
[CSid](../../atl/reference/csid-class.md)物件陣列的指標。

*pAccessMasks*<br/>
存取遮罩。

*pAceTypes*<br/>
存取控制專案 (ACE) 類型。

*pAceFlags*<br/>
ACE 旗標。

### <a name="remarks"></a>備註

這個方法會以`CAcl`物件中包含的每個 ACE 物件的詳細資料來填入陣列參數。 當不需要該特定陣列的詳細資料時, 請使用 Null。

每個陣列的內容彼此對應, 也就是說, `CAccessMaskArray`陣列的第一個元素會對應到`CSidArray`陣列中的第一個元素, 依此類推。

如需 ACE 類型和旗標的詳細資訊, 請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-ace_header) 。

##  <a name="getaclentry"></a>CAcl::GetAclEntry

抓取存取控制清單 (ACL) 中某個專案的所有相關資訊。

```
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要取出的 ACL 專案索引。

*pSid*<br/>
要套用 ACL 專案的[CSid](../../atl/reference/csid-class.md)物件。

*pMask*<br/>
遮罩, 指定授與或拒絕存取權的許可權。

*pType*<br/>
ACE 類型。

*pFlags*<br/>
ACE 旗標。

*pObjectType*<br/>
物件類型。 如果 ACE 中未指定物件類型, 或如果 ACE 不是物件 ACE, 這會設定為 GUID_Null。

*pInheritedObjectType*<br/>
繼承的物件類型。 如果未在 ACE 中指定繼承的物件類型, 或如果 ACE 不是物件 ACE, 這會設定為 GUID_Null。

### <a name="remarks"></a>備註

這個方法會抓取個別 ACE 的所有相關資訊, 並提供比[CAcl:: GetAclEntries](#getaclentries)單獨提供更多的資訊。

如需 ACE 類型和旗標的詳細資訊, 請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-ace_header) 。

##  <a name="getlength"></a>CAcl:: GetLength

傳回存取控制清單 (ACL) 的長度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>傳回值

傳回保存`ACL`結構所需的必要長度 (以位元組為單位)。

##  <a name="getpacl"></a>CAcl::GetPACL

傳回存取控制清單 (ACL) 的指標。

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>傳回值

傳回結構的`ACL`指標。

##  <a name="isempty"></a>CAcl:: IsEmpty

測試專案的物件。 `CAcl`

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>備註

如果`CAcl`物件不是 Null, 且不包含任何專案, 則傳回 TRUE。 如果`CAcl`物件為 Null, 或包含至少一個專案, 則傳回 FALSE。

##  <a name="isnull"></a>CAcl:: IsNull

傳回`CAcl`物件的狀態。

```
bool IsNull() const throw();
```

### <a name="return-value"></a>傳回值

如果`CAcl`物件為 Null, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="operator_const_acl__star"></a>CAcl:: operator const ACL *

將物件轉換`ACL`為 (存取控制清單) 結構。 `CAcl`

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>備註

傳回`ACL`結構的位址。

##  <a name="operator_eq"></a>CAcl:: operator =

指派運算子。

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`CAcl`指派給現有物件的。

### <a name="return-value"></a>傳回值

傳回已更新`CAcl`物件的參考。

##  <a name="removeace"></a>  CAcl::RemoveAce

從`CAcl`物件中移除特定的 ACE (存取控制專案)。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要移除之 ACE 專案的索引。

### <a name="remarks"></a>備註

這個方法衍生自[CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat)。

##  <a name="removeaces"></a>  CAcl::RemoveAces

從`CAcl`適用于指定`CSid`的, 移除的 alls ace (存取控制專案)。

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>參數

*rSid*<br/>
對 `CSid` 物件的參考。

##  <a name="setempty"></a>CAcl::SetEmpty

將`CAcl`物件標示為空白。

```
void SetEmpty() throw();
```

### <a name="remarks"></a>備註

`CAcl`可以設定為空白或 Null: 這兩個狀態是相異的。

##  <a name="setnull"></a>CAcl:: SetNull

將`CAcl`物件標記為 Null。

```
void SetNull() throw();
```

### <a name="remarks"></a>備註

`CAcl`可以設定為空白或 Null: 這兩個狀態是相異的。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)
