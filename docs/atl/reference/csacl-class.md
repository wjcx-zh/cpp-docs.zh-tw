---
title: CSacl 類別
ms.date: 11/04/2016
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
ms.openlocfilehash: b75dc4110b785f0ab1f55ba5c31df7d3fc6fbd37
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915748"
---
# <a name="csacl-class"></a>CSacl 類別

這個類別是 SACL (系統存取控制清單) 結構的包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CSacl : public CAcl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CSacl::CSacl](#csacl)|建構函式。|
|[CSacl::~CSacl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|將 audit 存取控制專案 (ACE) 新增至`CSacl`物件。|
|[CSacl::GetAceCount](#getacecount)|傳回`CSacl`物件中的存取控制專案 (ace) 數目。|
|[CSacl::RemoveAce](#removeace)|從`CSacl`物件中移除特定的 ACE (存取控制專案)。|
|[CSacl::RemoveAllAces](#removeallaces)|移除`CSacl`物件中包含的所有 ace。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CSacl:: operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

SACL 包含存取控制專案 (Ace), 可指定在網域控制站的安全性事件記錄檔中產生審核記錄的存取嘗試類型。 請注意, SACL 只會在發生存取嘗試的網域控制站, 而不是在包含物件複本的每個網域控制站上, 產生記錄檔專案。

若要設定或抓取物件安全描述項中的 SACL, 必須在要求的執行緒之存取權杖中啟用 SE_SECURITY_NAME 許可權。 [Administrators] 群組預設會授與此許可權, 而且可以授與其他使用者或群組。 已授與許可權並非所有必要動作: 可以執行許可權所定義的作業之前, 必須先在安全性存取權杖中啟用許可權, 才會生效。 此模型只允許針對特定的系統作業啟用許可權, 並在不再需要時停用。 如需啟用 SE_SECURITY_NAME 的範例, 請參閱[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl](security-global-functions.md#atlsetsacl) 。

使用提供的類別方法來新增、移除、建立和刪除物件中的`SACL` ace。 另請參閱[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl](security-global-functions.md#atlsetsacl)。

如需 Windows 中的存取控制模型簡介, 請參閱 Windows SDK 中的[存取控制](/windows/desktop/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CAcl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>需求

**標頭:** atlsecurity。h

##  <a name="addauditace"></a>CSacl::AddAuditAce

將 audit 存取控制專案 (ACE) 新增至`CSacl`物件。

```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>參數

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)物件。

*AccessMask*<br/>
指定要針對指定`CSid`物件進行審核的存取權限遮罩。

*bSuccess*<br/>
指定是否要審核允許的存取嘗試。 將此旗標設為 true 以啟用審核;否則, 請將它設定為 false。

*bFailure*<br/>
指定是否要審核拒絕的存取嘗試。 將此旗標設為 true 以啟用審核;否則, 請將它設定為 false。

*AceFlags*<br/>
控制 ACE 繼承的一組位旗標。

*pObjectType*<br/>
物件類型。

*pInheritedObjectType*<br/>
繼承的物件類型。

### <a name="return-value"></a>傳回值

如果 ACE 已加入至`CSacl`物件, 則傳回 TRUE, 否則會傳回 FALSE。

### <a name="remarks"></a>備註

`CSacl`物件包含存取控制專案 (ace), 可指定在安全性事件記錄檔中產生 audit 記錄的存取嘗試類型。 這個方法會將這類 ACE 新增`CSacl`至物件。

如需可在*AceFlags*參數中設定之各種旗標的說明, 請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-ace_header) 。

##  <a name="csacl"></a>  CSacl::CSacl

建構函式。

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
現有`ACL`的 (存取控制清單) 結構。

### <a name="remarks"></a>備註

您`CSacl`可以使用現有`ACL`的結構選擇性地建立物件。 請確定此參數是系統存取控制清單 (SACL), 而不是任意存取控制清單 (DACL)。 在 debug build 中, 如果提供了 DACL, 就會發生判斷提示。 在發行組建中, 會忽略 DACL 中的任何專案。

##  <a name="dtor"></a>  CSacl::~CSacl

解構函式。

```
~CSacl() throw();
```

### <a name="remarks"></a>備註

此析構函式會釋出物件所取得的任何資源, 包括所有存取控制專案 (Ace)。

##  <a name="getacecount"></a>  CSacl::GetAceCount

傳回`CSacl`物件中的存取控制專案 (ace) 數目。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回包含在`CSacl`物件中的 ace 數目。

##  <a name="operator_eq"></a>CSacl:: operator =

指派運算子。

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`ACL`指派給現有物件的 (存取控制清單)。

### <a name="return-value"></a>傳回值

傳回已更新`CSacl`物件的參考。 請確定參數實際上是系統存取控制清單 (SACL), 而不是任意存取控制清單 (DACL)。 `ACL` 在 debug build 中, 會發生判斷提示, 而且在發行`ACL`組建中, 將會忽略參數。

##  <a name="removeace"></a>  CSacl::RemoveAce

從`CSacl`物件中移除特定的 ACE (存取控制專案)。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要移除之 ACE 專案的索引。

### <a name="remarks"></a>備註

這個方法衍生自[CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat)。

##  <a name="removeallaces"></a>  CSacl::RemoveAllAces

移除`CSacl`物件中包含的所有存取控制專案 (ace)。

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>備註

移除物件`ACE`中的`CSacl`每個結構 (如果有的話)。

## <a name="see-also"></a>另請參閱

[CAcl 類別](../../atl/reference/cacl-class.md)<br/>
[Acl](/windows/desktop/SecAuthZ/access-control-lists)<br/>
[A](/windows/desktop/SecAuthZ/access-control-entries)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)
