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
ms.openlocfilehash: d5a060555901361ef6c70c6a4f801605eafd92cf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746559"
---
# <a name="csacl-class"></a>CSacl 類別

此類是 SACL(系統存取控制列表)結構的包裝器。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CSacl : public CAcl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSacl:CSacl](#csacl)|建構函式。|
|[CSacl:*CSacl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSacl::添加審核](#addauditace)|向`CSacl`物件添加審核存取控制項目 (ACE)。|
|[CSacl:取得服務計數](#getacecount)|返回`CSacl`物件中的訪問控制條目 (AES) 數。|
|[CSacl::刪除Ace](#removeace)|從`CSacl`物件中刪除特定的 ACE(訪問控制條目)。|
|[CSacl::刪除所有Aces](#removeallaces)|刪除`CSacl`物件中包含的所有 ACA。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CSacl::運算符 |](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

SACL 包含存取控制項目 (ACE),用於指定在網域控制器的安全事件日誌中生成審核記錄的存取嘗試類型。 請注意,SACL 僅在發生訪問嘗試的域控制器上生成日誌條目,而不是在包含物件副本的每個域控制器上生成日誌條目。

若要在物件的安全描述符中設置或檢索 SACL,必須在請求線程的訪問權杖中啟用SE_SECURITY_NAME許可權。 默認情況下,管理員組具有授予此許可權的許可權,可以授予其他使用者或組。 授予許可權並非全部必需:在可以執行許可權定義的操作之前,必須在安全訪問令牌中啟用該特權才能生效。 該模型允許僅針對特定的系統操作啟用特權,然後在不再需要特權時禁用這些許可權。 有關啟用SE_SECURITY_NAME的示例,請參閱[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl。](security-global-functions.md#atlsetsacl)

使用提供的類方法從`SACL`物件添加、刪除、創建和刪除 ACA。 另請參閱[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl](security-global-functions.md#atlsetsacl)。

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CAcl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="csacladdauditace"></a><a name="addauditace"></a>CSacl::添加審核

向`CSacl`物件添加審核存取控制項目 (ACE)。

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

*存取遮罩*<br/>
指定要審核指定`CSid`物件的訪問許可權的掩碼。

*b 成功*<br/>
指定是否審核允許的訪問嘗試。 將此標誌設置為 true 以啟用審核;否則,將其設置為 false。

*b 失敗*<br/>
指定是否審核被拒絕的訪問嘗試。 將此標誌設置為 true 以啟用審核;否則,將其設置為 false。

*王牌標誌*<br/>
控制ACE繼承的一組位標誌。

*pObject 類型*<br/>
物件類型。

*p 繼承物件類型*<br/>
繼承的物件類型。

### <a name="return-value"></a>傳回值

如果 ACE 添加到`CSacl`物件, 則傳回 TRUE,在失敗時傳回 FALSE。

### <a name="remarks"></a>備註

對`CSacl`象 包含存取控制項目 (ACE),用於指定在安全事件日誌中生成審核記錄的存取嘗試類型。 此方法向`CSacl`物件添加這樣的 ACE。

有關可在*AceFlags*參數中設置的各種標誌的說明,請參閱[ACE_HEADER。](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="csaclcsacl"></a><a name="csacl"></a>CSacl:CSacl

建構函式。

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
現有`ACL`(存取控制列表)結構。

### <a name="remarks"></a>備註

可以使用`CSacl`現有`ACL`結構選擇創建物件。 確保此參數是系統存取控制清單 (SACL),而不是任意存取控制列表 (DACL)。 在調試生成中,如果提供 DACL,將發生斷言。 在版本版本中,DACL 中的任何條目都將被忽略。

## <a name="csaclcsacl"></a><a name="dtor"></a>CSacl:*CSacl

解構函式。

```
~CSacl() throw();
```

### <a name="remarks"></a>備註

析構函數釋放物件獲取的任何資源,包括所有訪問控制條目 (ACE)。

## <a name="csaclgetacecount"></a><a name="getacecount"></a>CSacl:取得服務計數

返回`CSacl`物件中的訪問控制條目 (AES) 數。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>傳回值

返回`CSacl`物件中包含的 ACA 數。

## <a name="csacloperator-"></a><a name="operator_eq"></a>CSacl::運算符 |

指派運算子。

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`ACL`分配給現有物件的(訪問控制清單)。

### <a name="return-value"></a>傳回值

返回對更新`CSacl`物件的引用。 確保`ACL`參數實際上是一個系統存取控制列表 (SACL),而不是一個可自由的存取控制列表 (DACL)。 在調試生成中,將發生斷言,在發佈版本中,`ACL`參數將被忽略。

## <a name="csaclremoveace"></a><a name="removeace"></a>CSacl::刪除Ace

從`CSacl`物件中刪除特定的 ACE(訪問控制條目)。

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要刪除的 ACE 條目的索引。

### <a name="remarks"></a>備註

此方法派生自[CAtlarray::removeAt。](../../atl/reference/catlarray-class.md#removeat)

## <a name="csaclremoveallaces"></a><a name="removeallaces"></a>CSacl::刪除所有Aces

刪除`CSacl`物件中包含的所有訪問控制項目 (AES)。

```cpp
void RemoveAllAces() throw();
```

### <a name="remarks"></a>備註

刪除`CSacl``ACE`物件中的每個結構(如果有)。

## <a name="see-also"></a>另請參閱

[CAcl 類別](../../atl/reference/cacl-class.md)<br/>
[ACL](/windows/win32/SecAuthZ/access-control-lists)<br/>
[A](/windows/win32/SecAuthZ/access-control-entries)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全全域功能](../../atl/reference/security-global-functions.md)
