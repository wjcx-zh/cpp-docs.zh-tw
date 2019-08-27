---
title: CDacl 類別
ms.date: 11/04/2016
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
ms.openlocfilehash: a37ef47a4ea89d9ec24fac417e5b715bd2602fd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496935"
---
# <a name="cdacl-class"></a>CDacl 類別

這個類別是 DACL (任意存取控制清單) 結構的包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CDacl : public CAcl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|建構函式。|
|[CDacl::~CDacl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|將允許的 ACE (存取控制專案) 新增至`CDacl`物件。|
|[CDacl::AddDeniedAce](#adddeniedace)|將拒絕的 ACE 加入至`CDacl`物件。|
|[CDacl::GetAceCount](#getacecount)|傳回`CDacl`物件中的 ace (存取控制專案) 數目。|
|[CDacl::RemoveAce](#removeace)|從`CDacl`物件中移除特定的 ACE (存取控制專案)。|
|[CDacl::RemoveAllAces](#removeallaces)|移除`CDacl`物件中包含的所有 ace。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CDacl:: operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

物件的安全描述項可以包含 DACL。 DACL 包含零個或多個 Ace (存取控制專案), 用以識別可以存取物件的使用者和群組。 如果 DACL 是空的 (亦即, 它包含零個 Ace), 則不會明確授與存取權, 因此會隱含拒絕存取。 不過, 如果物件的安全描述項沒有 DACL, 物件就不受保護, 而且每個人都有完整的存取權。

若要取出物件的 DACL, 您必須是物件的擁有者, 或具有物件的 READ_CONTROL 存取權。 若要變更物件的 DACL, 您必須擁有物件的 WRITE_DAC 存取權。

使用提供的類別方法, 從`CDacl`物件建立、新增、移除和刪除 ace。 另請參閱[AtlGetDacl](security-global-functions.md#atlgetdacl)和[AtlSetDacl](security-global-functions.md#atlsetdacl)。

如需 Windows 中的存取控制模型簡介, 請參閱 Windows SDK 中的[存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>需求

**標頭:** atlsecurity。h

##  <a name="addallowedace"></a>CDacl::AddAllowedAce

將允許的 ACE (存取控制專案) 新增至`CDacl`物件。

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

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)物件。

*AccessMask*<br/>
為指定`CSid`的物件指定允許的存取權限遮罩。

*AceFlags*<br/>
控制 ACE 繼承的一組位旗標。

*pObjectType*<br/>
物件類型。

*pInheritedObjectType*<br/>
繼承的物件類型。

### <a name="return-value"></a>傳回值

如果 ACE 已加入至`CDacl`物件, 則傳回 TRUE, 否則會傳回 FALSE。

### <a name="remarks"></a>備註

`CDacl`物件包含零個或多個 ace (存取控制專案), 用以識別可以存取物件的使用者和群組。 這個方法會加入允許存取`CDacl`物件的 ACE。

如需可在`AceFlags`參數中設定之各種旗標的說明, 請參閱 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header)。

##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce

將拒絕的 ACE (存取控制專案) 新增至`CDacl`物件。

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

*rSid*<br/>
`CSid` 物件。

*AccessMask*<br/>
指定要拒絕之指定`CSid`物件的存取權限遮罩。

*AceFlags*<br/>
控制 ACE 繼承的一組位旗標。 在方法的第一種形式中, 預設為0。

*pObjectType*<br/>
物件類型。

*pInheritedObjectType*<br/>
繼承的物件類型。

### <a name="return-value"></a>傳回值

如果 ACE 已加入至`CDacl`物件, 則傳回 TRUE, 否則會傳回 FALSE。

### <a name="remarks"></a>備註

`CDacl`物件包含零個或多個 ace (存取控制專案), 用以識別可以存取物件的使用者和群組。 這個方法會加入一個 ACE, 以拒絕對`CDacl`物件的存取。

如需可在`AceFlags`參數中設定之各種旗標的說明, 請參閱 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header)。

##  <a name="cdacl"></a>  CDacl::CDacl

建構函式。

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>參數

*rhs*<br/>
現有`ACL`的 (存取控制清單) 結構。

### <a name="remarks"></a>備註

您`CDacl`可以使用現有`ACL`的結構選擇性地建立物件。 請務必注意, 只有 DACL (任意存取控制清單), 而不是 SACL (系統存取控制清單) 應當做此參數傳遞。 在 debug 組建中, 傳遞 SACL 會導致判斷提示。 在發行組建中, 傳遞 SACL 將會忽略 ACL 中的 Ace (存取控制專案), 而且不會發生錯誤。

##  <a name="dtor"></a>  CDacl::~CDacl

解構函式。

```
~CDacl () throw();
```

### <a name="remarks"></a>備註

此析構函式會釋放物件所取得的任何資源, 包括使用[CDacl:: RemoveAllAces](#removeallaces)的所有 ace (存取控制專案)。

##  <a name="getacecount"></a>  CDacl::GetAceCount

傳回`CDacl`物件中的 ace (存取控制專案) 數目。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回包含在`CDacl`物件中的 ace 數目。

##  <a name="operator_eq"></a>  CDacl::operator =

指派運算子。

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要指派給現有物件的 ACL (存取控制清單)。

### <a name="return-value"></a>傳回值

傳回已更新`CDacl`物件的參考。

### <a name="remarks"></a>備註

您應該確定只將 DACL (任意存取控制清單) 傳遞至此函式。 將 SACL (系統存取控制清單) 傳遞至這個函式會導致在 debug build 中使用判斷提示, 但不會在發行組建中產生錯誤。

##  <a name="removeace"></a>  CDacl::RemoveAce

從`CDacl`物件中移除特定的 ACE (存取控制專案)。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要移除之 ACE 專案的索引。

### <a name="remarks"></a>備註

這個方法衍生自[CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat)。

##  <a name="removeallaces"></a>  CDacl::RemoveAllAces

移除`CDacl`物件中包含的所有 ace (存取控制專案)。

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>備註

移除物件`ACE`中的`CDacl`每個 (存取控制專案) 結構 (如果有的話)。

## <a name="see-also"></a>另請參閱

[安全性範例](../../overview/visual-cpp-samples.md)<br/>
[CAcl 類別](../../atl/reference/cacl-class.md)<br/>
[Acl](/windows/win32/SecAuthZ/access-control-lists)<br/>
[A](/windows/win32/SecAuthZ/access-control-entries)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)
