---
title: CAcl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db7903dccfd851bb4bf76f1990424f887686d344
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070102"
---
# <a name="cacl-class"></a>CAcl 類別

這個類別是包裝函式`ACL`（存取控制清單） 結構。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class CAcl
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|ACCESS_MASKs 陣列。|
|[CAcl::CAceFlagArray](#caceflagarray)|位元組陣列。|
|[CAcl::CAceTypeArray](#cacetypearray)|位元組陣列。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|建構函式。|
|[CAcl:: ~ CAcl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|會傳回項目 (ACE) 物件的存取控制數目。|
|[CAcl::GetAclEntries](#getaclentries)|擷取存取控制清單 (ACL) 項目，從`CAcl`物件。|
|[CAcl::GetAclEntry](#getaclentry)|擷取所有的資訊中的項目`CAcl`物件。|
|[CAcl::GetLength](#getlength)|傳回 ACL 的長度。|
|[CAcl::GetPACL](#getpacl)|傳回 PACL （ACL 的指標）。|
|[CAcl::IsEmpty](#isempty)|測試`CAcl`物件的項目。|
|[CAcl::IsNull](#isnull)|傳回的狀態`CAcl`物件。|
|[CAcl::RemoveAce](#removeace)|移除特定的 ACE （存取控制項目）`CAcl`物件。|
|[CAcl::RemoveAces](#removeaces)|移除所有的 Ace （存取控制項目）`CAcl`套用到給定`CSid`。|
|[CAcl::SetEmpty](#setempty)|標記`CAcl`物件為空白。|
|[CAcl::SetNull](#setnull)|標記`CAcl`為 NULL 的物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAcl::operator const ACL *](#operator_const_acl__star)|轉型`CAcl`物件至`ACL`結構。|
|[CAcl::operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

`ACL`結構是 ACL （存取控制清單） 的標頭。 ACL 包含零或多個循序清單[Ace](/windows/desktop/SecAuthZ/access-control-entries) （存取控制項目）。 ACL 中的個別 Ace 會編號從 0 到*n-1*，其中*n*是在 ACL 中的 Ace 數目。 當您編輯 ACL，應用程式是指在 ACL 中存取控制項目 (ACE) 依其索引。

有兩種 ACL 類型：

- 判別

- 系統

判別 ACL 控制物件的擁有者或任何人都授與對物件的 WRITE_DAC 存取。 它會指定存取特定使用者和群組可以有的物件。 例如，檔案的擁有者可以使用判別 ACL 來控制哪些使用者及群組可以和不能有存取檔案。

物件也可以有與其相關聯，系統由系統管理員所控制的 ACL 的表單中的系統層級的安全性資訊。 系統 ACL 可以允許系統管理員稽核任何嘗試取得物件的存取權。

如需詳細資訊，請參閱 < [ACL](/windows/desktop/SecAuthZ/access-control-lists) Windows SDK 中的討論。

在 Windows 中的存取控制模型的簡介，請參閱 <<c0> [ 存取控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="requirements"></a>需求

**標頭：** atlsecurity.h

##  <a name="caccessmaskarray"></a>  CAcl::CAccessMaskArray

ACCESS_MASK 物件的陣列。

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>備註

此 typedef 會指定可以用來儲存使用的存取權限的存取控制項目 (Ace) 中的陣列類型。

##  <a name="caceflagarray"></a>  CAcl::CAceFlagArray

位元組陣列。

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>備註

此 typedef 指定用來定義存取控制項目 (ACE) 特定型別的控制旗標的陣列類型。 請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)定義可能的旗標的完整清單。

##  <a name="cacetypearray"></a>  CAcl::CAceTypeArray

位元組陣列。

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>備註

此 typedef 指定用來定義存取控制項目 (ACE) 物件，例如 ACCESS_ALLOWED_ACE_TYPE 或 ACCESS_DENIED_ACE_TYPE 性質的陣列類型。 請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)可能的型別定義的完整清單。

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

`CAcl`物件可以選擇性地建立使用現有`CAcl`物件。

##  <a name="dtor"></a>  CAcl:: ~ CAcl

解構函式。

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>備註

解構函式會釋放物件所取得的任何資源。

##  <a name="getacecount"></a>  CAcl::GetAceCount

會傳回項目 (ACE) 物件的存取控制數目。

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>傳回值

傳回的 ACE 中的項目數目`CAcl`物件。

##  <a name="getaclentries"></a>  CAcl::GetAclEntries

擷取存取控制清單 (ACL) 項目，從`CAcl`物件。

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSids*<br/>
陣列的指標[CSid](../../atl/reference/csid-class.md)物件。

*pAccessMasks*<br/>
存取遮罩。

*pAceTypes*<br/>
存取控制項目 (ACE) 型別。

*pAceFlags*<br/>
ACE 的旗標。

### <a name="remarks"></a>備註

這個方法會填入詳細資料中包含的每個 ACE 物件的陣列參數`CAcl`物件。 不需要該特定的陣列的詳細資料時，請使用 NULL。

每個陣列的內容對應到彼此，也就是第一個項目`CAccessMaskArray`陣列中的第一個項目對應`CSidArray`陣列，並依此類推。

請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)如需詳細資訊 ACE 型別和旗標。

##  <a name="getaclentry"></a>  CAcl::GetAclEntry

擷取所有的存取控制清單 (ACL) 中的項目有關的資訊。

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
若要擷取的 ACL 項目索引。

*pSid*<br/>
[CSid](../../atl/reference/csid-class.md) ACL 項目套用至物件。

*pMask*<br/>
指定權限授與或拒絕存取遮罩。

*pType*<br/>
ACE 型別。

*pFlags*<br/>
ACE 的旗標。

*pObjectType*<br/>
物件類型。 這會設定為 GUID_NULL，如果未指定的物件型別中的 ACE，或如果 ACE 不是物件 ACE。

*pInheritedObjectType*<br/>
繼承的物件型別。 這會設定為 GUID_NULL，如果未指定繼承的物件型別中的 ACE，或如果 ACE 不是物件 ACE。

### <a name="remarks"></a>備註

這個方法會擷取所有的個別 ACE，提供比的詳細資訊的相關資訊[CAcl::GetAclEntries](#getaclentries)單獨提供。

請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)如需詳細資訊 ACE 型別和旗標。

##  <a name="getlength"></a>  CAcl::GetLength

傳回的存取控制清單 (ACL) 的長度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>傳回值

傳回以位元組為單位的所需的長度來保存必要`ACL`結構。

##  <a name="getpacl"></a>  CAcl::GetPACL

讓指標回到存取控制清單 (ACL)。

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>傳回值

將指標傳回至`ACL`結構。

##  <a name="isempty"></a>  CAcl::IsEmpty

測試`CAcl`物件的項目。

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>備註

如果為 true`CAcl`物件不是 NULL，並包含任何項目。 如果傳回 FALSE`CAcl`物件為 NULL，或包含至少一個項目。

##  <a name="isnull"></a>  CAcl::IsNull

傳回的狀態`CAcl`物件。

```
bool IsNull() const throw();
```

### <a name="return-value"></a>傳回值

如果為 true`CAcl`物件可說是 NULL、 FALSE。

##  <a name="operator_const_acl__star"></a>  CAcl::operator const ACL *

轉型`CAcl`物件至`ACL`（存取控制清單） 結構。

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>備註

傳回的位址`ACL`結構。

##  <a name="operator_eq"></a>  CAcl::operator =

指派運算子。

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
`CAcl`指派給現有的物件。

### <a name="return-value"></a>傳回值

傳回已更新的參考`CAcl`物件。

##  <a name="removeace"></a>  CAcl::RemoveAce

移除特定的 ACE （存取控制項目）`CAcl`物件。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>參數

*nIndex*<br/>
若要移除的 ACE 項目索引。

### <a name="remarks"></a>備註

這個方法衍生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。

##  <a name="removeaces"></a>  CAcl::RemoveAces

移除 alls （存取控制項目） 的 Ace`CAcl`套用到給定`CSid`。

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>參數

*rSid*<br/>
對 `CSid` 物件的參考。

##  <a name="setempty"></a>  CAcl::SetEmpty

標記`CAcl`物件為空白。

```
void SetEmpty() throw();
```

### <a name="remarks"></a>備註

`CAcl`可以設定為空白或為 NULL： 兩個狀態就會不同。

##  <a name="setnull"></a>  CAcl::SetNull

標記`CAcl`為 NULL 的物件。

```
void SetNull() throw();
```

### <a name="remarks"></a>備註

`CAcl`可以設定為空白或為 NULL： 兩個狀態就會不同。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)
