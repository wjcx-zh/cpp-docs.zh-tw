---
title: "CAcl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 52de083664c2e9ca00a140450cb43372aff28428
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cacl-class"></a>CAcl 類別
這個類別是包裝函式`ACL`（存取控制清單） 的結構。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAcl
```  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CAcl::CAccessMaskArray](#caccessmaskarray)|陣列`ACCESS_MASK`s。|  
|[CAcl::CAceFlagArray](#caceflagarray)|陣列`BYTE`s。|  
|[CAcl::CAceTypeArray](#cacetypearray)|陣列`BYTE`s。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAcl::CAcl](#cacl)|建構函式。|  
|[CAcl:: ~ CAcl](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAcl::GetAceCount](#getacecount)|傳回項目 (ACE) 物件的存取控制的數目。|  
|[CAcl::GetAclEntries](#getaclentries)|擷取存取控制清單 (ACL) 項目從`CAcl`物件。|  
|[CAcl::GetAclEntry](#getaclentry)|擷取所有的資訊中的項目`CAcl`物件。|  
|[CAcl::GetLength](#getlength)|傳回之 ACL 的長度。|  
|[CAcl::GetPACL](#getpacl)|傳回 PACL （指標的 acl）。|  
|[CAcl::IsEmpty](#isempty)|測試`CAcl`物件的項目。|  
|[CAcl::IsNull](#isnull)|傳回的狀態，`CAcl`物件。|  
|[CAcl::RemoveAce](#removeace)|移除特定的 ACE （存取控制的項目）`CAcl`物件。|  
|[CAcl::RemoveAces](#removeaces)|移除所有 Ace （存取控制的項目）`CAcl`套用到給定`CSid`。|  
|[CAcl::SetEmpty](#setempty)|標記`CAcl`物件為空白。|  
|[CAcl::SetNull](#setnull)|標記`CAcl`物件做為`NULL`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CAcl::operator const ACL *](#operator_const_acl__star)|轉換 （cast)`CAcl`物件傳遞給`ACL`結構。|  
|[CAcl::operator =](#operator_eq)|指派運算子。|  
  
## <a name="remarks"></a>備註  
 **ACL**結構是 ACL （存取控制清單） 的標頭。 ACL 包含零或多個循序清單[Ace](http://msdn.microsoft.com/library/windows/desktop/aa374868) （存取控制的項目）。 ACL 中的個別 Ace 會編號從 0 到*n-1*，其中*n*是在 ACL 中的 Ace 數目。 當編輯 ACL，應用程式是指在 ACL 中存取控制項目 (ACE) 依其索引。  
  
 有兩種 ACL 類型︰  
  
-   判別  
  
-   系統  
  
 判別 ACL 控制物件的擁有者或任何人都獲得**WRITE_DAC**物件的存取權。 它會指定存取特定使用者和群組可以擁有物件。 例如，檔案的擁有者可以使用判別 ACL，以控制哪些使用者及群組可以和無法用來存取檔案。  
  
 物件也可以有與其相關聯，系統由系統管理員所控制的 ACL 的表單中的系統層級的安全性資訊。 系統 ACL 可以允許系統管理員稽核任何嘗試取得物件的存取權。  
  
 如需詳細資訊，請參閱[ACL](http://msdn.microsoft.com/library/windows/desktop/aa374872)中的討論[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h  
  
##  <a name="caccessmaskarray"></a>CAcl::CAccessMaskArray  
 ACCESS_MASK 物件的陣列。  
  
```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```  
  
### <a name="remarks"></a>備註  
 此 typedef 指定陣列型別可以用來存放存取控制項目 (Ace) 中使用的存取權限。  
  
##  <a name="caceflagarray"></a>CAcl::CAceFlagArray  
 位元組陣列。  
  
```
typedef CAtlArray<BYTE> CAceFlagArray;
```  
  
### <a name="remarks"></a>備註  
 此 typedef 指定用來定義存取控制項目 (ACE) 特定類型的控制旗標的陣列類型。 請參閱[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)可能的旗標的完整清單定義。  
  
##  <a name="cacetypearray"></a>CAcl::CAceTypeArray  
 位元組陣列。  
  
```
typedef CAtlArray<BYTE> CAceTypeArray;
```  
  
### <a name="remarks"></a>備註  
 此 typedef 指定用來定義存取控制項目 (ACE) 物件，例如 ACCESS_ALLOWED_ACE_TYPE 或 ACCESS_DENIED_ACE_TYPE 性質的陣列類型。 請參閱[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)可能的型別定義的完整清單。  
  
##  <a name="cacl"></a>CAcl::CAcl  
 建構函式。  
  
```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 現有的 `CAcl` 物件。  
  
### <a name="remarks"></a>備註  
 `CAcl`物件，可選擇性地建立使用現有`CAcl`物件。  
  
##  <a name="dtor"></a>CAcl:: ~ CAcl  
 解構函式。  
  
```
virtual ~CAcl() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放物件所取得的任何資源。  
  
##  <a name="getacecount"></a>CAcl::GetAceCount  
 傳回項目 (ACE) 物件的存取控制的數目。  
  
```
virtual UINT GetAceCount() const throw() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 傳回的 ACE 中的項目數`CAcl`物件。  
  
##  <a name="getaclentries"></a>CAcl::GetAclEntries  
 擷取存取控制清單 (ACL) 項目從`CAcl`物件。  
  
```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```  
  
### <a name="parameters"></a>參數  
 `pSids`  
 陣列的指標[CSid](../../atl/reference/csid-class.md)物件。  
  
 *pAccessMasks*  
 存取遮罩中。  
  
 *pAceTypes*  
 存取控制項目 ( **ACE**) 型別。  
  
 *pAceFlags*  
 **ACE**旗標。  
  
### <a name="remarks"></a>備註  
 這個方法會填入陣列參數的詳細資料的每個**ACE**中所含物件`CAcl`物件。 當不需要該特定的陣列的詳細資訊，請使用 NULL。  
  
 每個陣列的內容對應到彼此，也就是第一個項目`CAccessMaskArray`陣列中的第一個項目對應`CSidArray`，依此類推。  
  
 請參閱[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)如需有關 ACE 型別和旗標。  
  
##  <a name="getaclentry"></a>CAcl::GetAclEntry  
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
 `nIndex`  
 若要擷取的 ACL 項目編製索引。  
  
 `pSid`  
 [CSid](../../atl/reference/csid-class.md)物件套用 ACL 項目。  
  
 *pMask*  
 指定權限授與或拒絕存取遮罩。  
  
 `pType`  
 ACE 類型。  
  
 `pFlags`  
 ACE 的旗標。  
  
 `pObjectType`  
 物件類型。 這會設定為 GUID_NULL，如果未指定的物件型別中的 ACE，或如果 ACE 不是物件 ACE。  
  
 `pInheritedObjectType`  
 繼承的物件類型。 這會設定為 GUID_NULL，如果未指定繼承的物件類型中的 ACE，或如果 ACE 不是物件 ACE。  
  
### <a name="remarks"></a>備註  
 這個方法會擷取個別的 ACE，提供比的詳細資訊的相關資訊的所有[CAcl::GetAclEntries](#getaclentries)單獨提供。  
  
 請參閱[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)如需有關 ACE 型別和旗標。  
  
##  <a name="getlength"></a>CAcl::GetLength  
 傳回的存取控制清單 (ACL) 的長度。  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回所需的長度以位元組為單位來保存所需**ACL**結構。  
  
##  <a name="getpacl"></a>CAcl::GetPACL  
 存取控制清單 (ACL) 傳回的指標。  
  
```
const ACL* GetPACL() const throw(...);
```  
  
### <a name="return-value"></a>傳回值  
 傳回的指標**ACL**結構。  
  
##  <a name="isempty"></a>CAcl::IsEmpty  
 測試`CAcl`物件的項目。  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回**true**如果`CAcl`物件不是 NULL，且不含項目。 傳回**false**如果`CAcl`物件為 NULL，或是包含至少一個項目。  
  
##  <a name="isnull"></a>CAcl::IsNull  
 傳回的狀態，`CAcl`物件。  
  
```
bool IsNull() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果`CAcl`物件為 NULL， **false**否則。  
  
##  <a name="operator_const_acl__star"></a>CAcl::operator const ACL *  
 轉換 （cast)`CAcl`物件傳遞給**ACL** （存取控制清單） 的結構。  
  
```  
operator const ACL *() const throw(...);
```  
  
### <a name="remarks"></a>備註  
 傳回的位址**ACL**結構。  
  
##  <a name="operator_eq"></a>CAcl::operator =  
 指派運算子。  
  
```
CAcl& operator= (const CAcl& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 `CAcl`將指派給現有的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回參考更新的`CAcl`物件。  
  
##  <a name="removeace"></a>CAcl::RemoveAce  
 移除特定的 ACE （存取控制的項目） **CAcl**物件。  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 若要移除 ACE 的項目編製索引。  
  
### <a name="remarks"></a>備註  
 這個方法衍生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。  
  
##  <a name="removeaces"></a>CAcl::RemoveAces  
 移除 alls Ace （存取控制的項目）`CAcl`套用到給定`CSid`。  
  
```
bool RemoveAces(const CSid& rSid) throw(...)
```  
  
### <a name="parameters"></a>參數  
 `rSid`  
 對 `CSid` 物件的參考。  
  
##  <a name="setempty"></a>CAcl::SetEmpty  
 標記`CAcl`物件為空白。  
  
```
void SetEmpty() throw();
```  
  
### <a name="remarks"></a>備註  
 `CAcl`可以設定為空白或為 NULL︰ 截然不同的兩個狀態。  
  
##  <a name="setnull"></a>CAcl::SetNull  
 標記`CAcl`物件為 NULL。  
  
```
void SetNull() throw();
```  
  
### <a name="remarks"></a>備註  
 `CAcl`可以設定為空白或為 NULL︰ 截然不同的兩個狀態。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性的全域函式](../../atl/reference/security-global-functions.md)

