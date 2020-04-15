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
ms.openlocfilehash: 87bf903220a584798ea59c5f1c701fc35049e901
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321663"
---
# <a name="cacl-class"></a>CAcl 類別

此類是`ACL`(訪問控制列表)結構的包裝器。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAcl
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CAcl:CAccessMaskarray](#caccessmaskarray)|ACCESS_MASKs陣列。|
|[Acl:CAceFlagarray](#caceflagarray)|BYTEs 的陣列。|
|[Acl:CAceTypearray](#cacetypearray)|BYTEs 的陣列。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Acl:CAcl](#cacl)|建構函式。|
|[CAcl:_CAcl](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Acl:取得AceCount](#getacecount)|返回訪問控制項目 (ACE) 物件的數量。|
|[Acl:取得 Acl](#getaclentries)|從`CAcl`物件檢索存取控制清單 (ACL) 項目。|
|[Acl:取得 Aclentry](#getaclentry)|檢索有關`CAcl`物件中條目的所有資訊。|
|[Acl:取得長度](#getlength)|返回 ACL 的長度。|
|[Acl:GetPACL](#getpacl)|返回 PACL(指向 ACL 的指標)。|
|[Acl:為空](#isempty)|測試`CAcl`物件為條目。|
|[Acl:IsNull](#isnull)|返回`CAcl`物件的狀態。|
|[Acl:移除Ace](#removeace)|從`CAcl`物件中刪除特定的 ACE(訪問控制條目)。|
|[Acl:移除 Ace](#removeaces)|從 中刪除應用於給`CAcl``CSid`定 的所有 ACE(訪問控制條目)。|
|[Acl:設定空](#setempty)|將`CAcl`物件標記為空。|
|[Acl:設定 Null](#setnull)|將`CAcl`物件標記為 NULL。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[Acl::運算符配置 ACL |](#operator_const_acl__star)|將`CAcl`對象強制轉換`ACL`為結構。|
|[CAcl::運算符 |](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

結構`ACL`是 ACL(訪問控制清單)的標頭。 ACL 包括零個或多個[ACE(](/windows/win32/SecAuthZ/access-control-entries)存取控制條目)的順序表。 ACL 中的單個 ACEs 編號為 0 到*n-1,* 其中*n*是 ACL 中的 ACEs 數。 編輯 ACL 時,應用程式透過索引引用 ACL 中的存取控制項目 (ACE)。

有兩種 ACL 類型:

- 酌情

- 系統

可自由存取的 ACL 由物件的擁有者或授予WRITE_DAC存取該物件的任何人控制。 它指定特定使用者和組對對象的訪問。 例如,檔案的擁有者可以使用任意 ACL 來控制哪些使用者和組可以並且不能存取該檔。

物件還可以以系統管理員控制的系統 ACL 的形式與其關聯系統級安全資訊。 系統 ACL 可以允許系統管理員審核任何訪問對象的嘗試。

有關詳細資訊,請參閱 Windows SDK 中的[ACL](/windows/win32/SecAuthZ/access-control-lists)討論。

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CAcl:CAccessMaskarray

ACCESS_MASK對象的陣組。

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>備註

此 typedef 指定可用於儲存存取控制項目 (ACE) 中使用的存取權限的陣列類型。

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a>Acl:CAceFlagarray

BYTEs 的陣列。

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>備註

此 typedef 指定用於定義存取控制項目 (ACE) 類型特定的控制標誌的陣列類型。 有關可能的標誌的完整清單,請參閱[ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header)定義。

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a>Acl:CAceTypearray

BYTEs 的陣列。

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>備註

此 typedef 指定用於定義存取控制項目 (ACE) 物件(如ACCESS_ALLOWED_ACE_TYPE或ACCESS_DENIED_ACE_TYPE)性質的陣列類型。 有關可能類型的完整清單,請參閱[ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header)定義。

## <a name="caclcacl"></a><a name="cacl"></a>Acl:CAcl

建構函式。

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
現有的 `CAcl` 物件。

### <a name="remarks"></a>備註

可以使用`CAcl`現有`CAcl`物件選擇創建該物件。

## <a name="caclcacl"></a><a name="dtor"></a>CAcl:_CAcl

解構函式。

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>備註

析構函數釋放對象獲取的任何資源。

## <a name="caclgetacecount"></a><a name="getacecount"></a>Acl:取得AceCount

返回訪問控制項目 (ACE) 物件的數量。

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>傳回值

返回`CAcl`物件中的 ACE 條目數。

## <a name="caclgetaclentries"></a><a name="getaclentries"></a>Acl:取得 Acl

從`CAcl`物件檢索存取控制清單 (ACL) 項目。

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>參數

*pSids*<br/>
指向[CSid](../../atl/reference/csid-class.md)物件陣列的指標。

*pAccess 遮罩*<br/>
訪問掩碼。

*pAce 類型*<br/>
訪問控制項目 (ACE) 類型。

*pAceFlags*<br/>
ACE 標誌。

### <a name="remarks"></a>備註

此方法使用`CAcl`物件中包含的每個ACE物件的詳細資訊填充陣列參數。 當不需要該特定陣列的詳細資訊時,請使用 NULL。

每個陣列的內容彼此對應,即`CAccessMaskArray`陣列的第一個元素對應於`CSidArray`陣列中的第一個元素,等等。

有關 ACE 類型和標誌的更多詳細資訊[,請參閱ACE_HEADER。](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="caclgetaclentry"></a><a name="getaclentry"></a>Acl:取得 Aclentry

檢索有關存取控制清單 (ACL) 中條目的所有資訊。

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
要檢索的 ACL 條目的索引。

*pSid*<br/>
ACL 項目應用於的[CSid](../../atl/reference/csid-class.md)物件。

*pMask*<br/>
指定授予或拒絕存取許可權的掩碼。

*p 型態*<br/>
ACE 類型。

*pFlags*<br/>
ACE 標誌。

*pObject 類型*<br/>
物件類型。 如果未在 ACE 中指定物件類型,或者 ACE 不是物件 ACE,則將設置為GUID_NULL。

*p 繼承物件類型*<br/>
繼承的物件類型。 如果 ACE 中未指定繼承的物件類型,或者 ACE 不是物件 ACE,則將設置為GUID_NULL。

### <a name="remarks"></a>備註

此方法將檢索有關單個 ACE 的所有資訊,提供比[僅提供 CAcl:getAcl 條目](#getaclentries)提供的資訊更多的資訊。

有關 ACE 類型和標誌的更多詳細資訊[,請參閱ACE_HEADER。](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="caclgetlength"></a><a name="getlength"></a>Acl:取得長度

返回訪問控制清單 (ACL) 的長度。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>傳回值

返回保存`ACL`結構所需的長度(以位元組為單位)。

## <a name="caclgetpacl"></a><a name="getpacl"></a>Acl:GetPACL

返回指向存取控制清單 (ACL) 的指標。

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>傳回值

返回指向結構的`ACL`指標。

## <a name="caclisempty"></a><a name="isempty"></a>Acl:為空

測試`CAcl`物件為條目。

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>備註

如果`CAcl`物件不是 NULL,並且不包含任何條目,則返回 TRUE。 如果`CAcl`物件為 NULL 或至少包含一個條目,則返回 FALSE。

## <a name="caclisnull"></a><a name="isnull"></a>Acl:IsNull

返回`CAcl`物件的狀態。

```
bool IsNull() const throw();
```

### <a name="return-value"></a>傳回值

如果物件為`CAcl`NULL,則傳回 TRUE,否則返回 FALSE。

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>Acl::運算符配置 ACL |

將`CAcl`物件強制轉換`ACL`為 (訪問控制列表)結構。

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>備註

傳回結構的`ACL`位址 。

## <a name="cacloperator-"></a><a name="operator_eq"></a>CAcl::運算符 |

指派運算子。

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
`CAcl`要分配給現有物件。

### <a name="return-value"></a>傳回值

返回對更新`CAcl`物件的引用。

## <a name="caclremoveace"></a><a name="removeace"></a>Acl:移除Ace

從`CAcl`物件中刪除特定的 ACE(訪問控制條目)。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要刪除的 ACE 條目的索引。

### <a name="remarks"></a>備註

此方法派生自[CAtlarray::removeAt。](../../atl/reference/catlarray-class.md#removeat)

## <a name="caclremoveaces"></a><a name="removeaces"></a>Acl:移除 Ace

從 中刪除應用於給`CAcl``CSid`定 的所有 ACE(訪問控制條目)。

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>參數

*rSid*<br/>
`CSid` 物件的參考。

## <a name="caclsetempty"></a><a name="setempty"></a>Acl:設定空

將`CAcl`物件標記為空。

```
void SetEmpty() throw();
```

### <a name="remarks"></a>備註

`CAcl`可以設置為空或 NULL:兩種狀態是截然不同的。

## <a name="caclsetnull"></a><a name="setnull"></a>Acl:設定 Null

將`CAcl`物件標記為 NULL。

```
void SetNull() throw();
```

### <a name="remarks"></a>備註

`CAcl`可以設置為空或 NULL:兩種狀態是截然不同的。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全全域功能](../../atl/reference/security-global-functions.md)
