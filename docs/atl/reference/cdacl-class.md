---
title: CDacl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3ce384c2478359b3496aa2d816a30e9a240c998
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760740"
---
# <a name="cdacl-class"></a>CDacl 類別

這個類別是 DACL （判別存取控制清單） 結構的包裝函式。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class CDacl : public CAcl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|建構函式。|
|[CDacl::~CDacl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|將允許的 ACE （存取控制項目） 加入至`CDacl`物件。|
|[CDacl::AddDeniedAce](#adddeniedace)|新增拒絕的 ACE`CDacl`物件。|
|[CDacl::GetAceCount](#getacecount)|會以傳回 （存取控制項目） 的 Ace 數目`CDacl`物件。|
|[CDacl::RemoveAce](#removeace)|移除特定的 ACE （存取控制項目）`CDacl`物件。|
|[CDacl::RemoveAllAces](#removeallaces)|移除所有的 Ace 中包含`CDacl`物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CDacl::operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

物件的安全性描述元可以包含 DACL。 DACL 包含零個或多個 Ace （存取控制項目） 所識別的使用者和群組可以存取的物件。 如果是空的 DACL （也就是包含零個 Ace），不明確授與存取權，因此會隱含拒絕存取。 不過，如果物件的安全性描述元，並沒有 DACL，物件是未受保護，而且每個人都有完整存取權。

若要擷取物件的 DACL，您必須是物件的擁有者，或具有 READ_CONTROL 物件的存取權。 若要變更物件的 DACL，您必須對物件的 WRITE_DAC 存取。

使用類別方法，可建立、 新增、 移除和刪除從 Ace`CDacl`物件。 另請參閱[AtlGetDacl](security-global-functions.md#atlgetdacl)並[AtlSetDacl](security-global-functions.md#atlsetdacl)。

在 Windows 中的存取控制模型的簡介，請參閱 <<c0> [ 存取控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="inheritance-hierarchy"></a>繼承階層

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>需求

**標頭：** atlsecurity.h

##  <a name="addallowedace"></a>  CDacl::AddAllowedAce

將允許的 ACE （存取控制項目） 加入至`CDacl`物件。

```
bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>參數

*rSid*  
A [CSid](../../atl/reference/csid-class.md)物件。

*AccessMask*  
指定允許的存取權限遮罩指定`CSid`物件。

*AceFlags*  
一組控制 ACE 繼承的位元旗標。

*pObjectType*  
物件類型。

*pInheritedObjectType*  
繼承的物件型別。

### <a name="return-value"></a>傳回值

會傳回 TRUE，如果 ACE 新增至`CDacl`物件，FALSE 失敗。

### <a name="remarks"></a>備註

A`CDacl`物件包含零個或多個 Ace （存取控制項目） 所識別的使用者和群組可以存取的物件。 這個方法會加入 ACE 允許存取`CDacl`物件。

請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)如需可以在中設定各種旗標的描述`AceFlags`參數。

##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce

將拒絕的 ACE （存取控制項目） 加入至`CDacl`物件。

```
bool AddDeniedAce(  
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>參數

*rSid*  
`CSid` 物件。

*AccessMask*  
指定要拒絕的存取權限遮罩指定`CSid`物件。

*AceFlags*  
一組控制 ACE 繼承的位元旗標。 預設為 0，在第一種形式的方法。

*pObjectType*  
物件類型。

*pInheritedObjectType*  
繼承的物件型別。

### <a name="return-value"></a>傳回值

會傳回 TRUE，如果 ACE 新增至`CDacl`物件，FALSE 失敗。

### <a name="remarks"></a>備註

A`CDacl`物件包含零個或多個 Ace （存取控制項目） 所識別的使用者和群組可以存取的物件。 此方法會將拒絕權限的 ACE`CDacl`物件。

請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)如需可以在中設定各種旗標的描述`AceFlags`參數。

##  <a name="cdacl"></a>  CDacl::CDacl

建構函式。

```
CDacl (const ACL& rhs) throw(...);  
CDacl () throw();
```

### <a name="parameters"></a>參數

*rhs*  
將現有`ACL`（存取控制清單） 結構。

### <a name="remarks"></a>備註

`CDacl`物件可以選擇性地建立使用現有`ACL`結構。 請務必請注意，只有 DACL （判別存取控制清單），而且不 SACL （系統存取控制清單），會傳遞作為此參數。 在偵錯組建中傳遞 SACL 會判斷提示。 在發行組建中傳遞 SACL 會導致 Ace （存取控制項目） 中的 ACL 會被忽略，且不會發生錯誤。

##  <a name="dtor"></a>  CDacl::~CDacl

解構函式。

```
~CDacl () throw();
```

### <a name="remarks"></a>備註

解構函式會取得物件，包括所有的 Ace （存取控制項目） 所使用的任何資源釋出[CDacl::RemoveAllAces](#removeallaces)。

##  <a name="getacecount"></a>  CDacl::GetAceCount

會以傳回 （存取控制項目） 的 Ace 數目`CDacl`物件。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回中所包含的 Ace 數目`CDacl`物件。

##  <a name="operator_eq"></a>  CDacl::operator =

指派運算子。

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*  
指派給現有的物件 ACL （存取控制清單）。

### <a name="return-value"></a>傳回值

傳回已更新的參考`CDacl`物件。

### <a name="remarks"></a>備註

您應該確定您只傳遞給此函式的 DACL （判別存取控制清單）。 傳遞 SACL （系統存取控制清單） 對此函式會導致偵錯組建中的判斷提示，但會導致任何錯誤，發行組建中。

##  <a name="removeace"></a>  CDacl::RemoveAce

移除特定的 ACE （存取控制項目）`CDacl`物件。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>參數

*nIndex*  
若要移除的 ACE 項目索引。

### <a name="remarks"></a>備註

這個方法衍生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。

##  <a name="removeallaces"></a>  CDacl::RemoveAllAces

移除所有的 Ace （存取控制項目） 中包含`CDacl`物件。

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>備註

移除每個`ACE`（存取控制項目） （如果有的話） 結構中的`CDacl`物件。

## <a name="see-also"></a>另請參閱

[安全性範例](../../visual-cpp-samples.md)   
[CAcl 類別](../../atl/reference/cacl-class.md)   
[Acl](/windows/desktop/SecAuthZ/access-control-lists)   
[Ace](/windows/desktop/SecAuthZ/access-control-entries)   
[類別概觀](../../atl/atl-class-overview.md)   
[安全性全域函式](../../atl/reference/security-global-functions.md)
