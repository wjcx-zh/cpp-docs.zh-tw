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
ms.openlocfilehash: 1540c90e3538d763708e161ba6c1a5e459bb2bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327144"
---
# <a name="cdacl-class"></a>CDacl 類別

此類是 DACL(自由存取控制列表)結構的包裝器。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CDacl : public CAcl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDacl:CDacl](#cdacl)|建構函式。|
|[CDacl:*CDacl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDacl::新增允許的Ace](#addallowedace)|向物件添加允許的`CDacl`ACE(訪問控制條目)。|
|[CDacl::添加否認](#adddeniedace)|向物件添加被拒絕的`CDacl`ACE。|
|[CDacl::取得服務計數](#getacecount)|傳回物件的 ACE(存取控制項目`CDacl`)數 。|
|[CDacl::刪除Ace](#removeace)|從`CDacl`物件中刪除特定的 ACE(訪問控制條目)。|
|[CDacl::刪除所有Aces](#removeallaces)|刪除`CDacl`物件中包含的所有 ACA。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CDacl::運算符 |](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

物件的安全描述符可以包含 DACL。 DACL 包含零個或多個 ACE(訪問控制條目),用於標識可以存取該物件的使用者和組。 如果 DACL 為空(即它包含零 ACEs),則不會顯式授予訪問許可權,因此隱式拒絕訪問。 但是,如果物件的安全描述符沒有 DACL,則該物件不受保護,並且每個人都可以完全訪問。

若要檢索物件的 DACL,您必須是物件的擁有者,或具有對該物件的READ_CONTROL訪問許可權。 要更改物件的 DACL,必須具有對該物件的WRITE_DAC訪問許可權。

使用提供的類方法從`CDacl`物件創建、添加、刪除和刪除 A。 另見[AtlGetDacl](security-global-functions.md#atlgetdacl)和[AtlSetDacl](security-global-functions.md#atlsetdacl)。

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="cdacladdallowedace"></a><a name="addallowedace"></a>CDacl::新增允許的Ace

向物件添加允許的`CDacl`ACE(訪問控制條目)。

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

*存取遮罩*<br/>
指定指定`CSid`物件允許的訪問許可權的掩碼。

*王牌標誌*<br/>
控制ACE繼承的一組位標誌。

*pObject 類型*<br/>
物件類型。

*p 繼承物件類型*<br/>
繼承的物件類型。

### <a name="return-value"></a>傳回值

如果 ACE 添加到`CDacl`物件, 則傳回 TRUE,在失敗時傳回 FALSE。

### <a name="remarks"></a>備註

物件`CDacl`包含零個或多個 ACE(訪問控制條目),用於標識可以存取該物件的使用者和組。 此方法添加了允許訪問`CDacl`物件的 ACE。

有關可在`AceFlags`參數中設置的各種標誌的說明,請參閱[ACE_HEADER。](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="cdacladddeniedace"></a><a name="adddeniedace"></a>CDacl::添加否認

向物件添加被拒絕的`CDacl`ACE(訪問控制條目)。

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

*存取遮罩*<br/>
指定要拒絕指定`CSid`物件的訪問許可權的掩碼。

*王牌標誌*<br/>
控制ACE繼承的一組位標誌。 在方法的第一種形式中預設為 0。

*pObject 類型*<br/>
物件類型。

*p 繼承物件類型*<br/>
繼承的物件類型。

### <a name="return-value"></a>傳回值

如果 ACE 添加到`CDacl`物件, 則傳回 TRUE,在失敗時傳回 FALSE。

### <a name="remarks"></a>備註

物件`CDacl`包含零個或多個 ACE(訪問控制條目),用於標識可以存取該物件的使用者和組。 此方法添加拒絕訪問`CDacl`物件的 ACE。

有關可在`AceFlags`參數中設置的各種標誌的說明,請參閱[ACE_HEADER。](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="cdaclcdacl"></a><a name="cdacl"></a>CDacl:CDacl

建構函式。

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>參數

*rhs*<br/>
現有`ACL`(存取控制列表)結構。

### <a name="remarks"></a>備註

可以使用`CDacl`現有`ACL`結構選擇創建物件。 請務必注意,應僅傳遞 DACL(自由存取控制清單),而不是 SACL(系統存取控制清單)。作為此參數傳遞。 在調試生成中,傳遞 SACL 將導致 ASSERT。 在發佈版本中,傳遞 SACL 將導致 ACL 中的 ACE(訪問控制條目)被忽略,並且不會發生錯誤。

## <a name="cdaclcdacl"></a><a name="dtor"></a>CDacl:*CDacl

解構函式。

```
~CDacl () throw();
```

### <a name="remarks"></a>備註

析構函數釋放物件獲取的任何資源,包括使用[CDacl::::removeAllAce](#removeallaces)的所有 ACE(訪問控制條目)。

## <a name="cdaclgetacecount"></a><a name="getacecount"></a>CDacl::取得服務計數

傳回物件的 ACE(存取控制項目`CDacl`)數 。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>傳回值

返回`CDacl`物件中包含的 ACA 數。

## <a name="cdacloperator-"></a><a name="operator_eq"></a>CDacl::運算符 |

指派運算子。

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要分配給現有物件的 ACL(存取控制清單)。

### <a name="return-value"></a>傳回值

返回對更新`CDacl`物件的引用。

### <a name="remarks"></a>備註

應確保僅將 DACL(自由存取控制列表)傳遞給此函數。 將 SACL(系統存取控制列表)傳遞給此函數將導致調試版本中的 ASSERT,但不會在發佈版本中造成錯誤。

## <a name="cdaclremoveace"></a><a name="removeace"></a>CDacl::刪除Ace

從`CDacl`物件中刪除特定的 ACE(訪問控制條目)。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要刪除的 ACE 條目的索引。

### <a name="remarks"></a>備註

此方法派生自[CAtlarray::removeAt。](../../atl/reference/catlarray-class.md#removeat)

## <a name="cdaclremoveallaces"></a><a name="removeallaces"></a>CDacl::刪除所有Aces

刪除`CDacl`物件中包含的所有 ACE(訪問控制條目)。

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>備註

刪除`CDacl``ACE`物件 中的每個(訪問控制條目)結構(如果有)。

## <a name="see-also"></a>另請參閱

[安全範例](../../overview/visual-cpp-samples.md)<br/>
[CAcl 類別](../../atl/reference/cacl-class.md)<br/>
[ACL](/windows/win32/SecAuthZ/access-control-lists)<br/>
[A](/windows/win32/SecAuthZ/access-control-entries)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全全域功能](../../atl/reference/security-global-functions.md)
