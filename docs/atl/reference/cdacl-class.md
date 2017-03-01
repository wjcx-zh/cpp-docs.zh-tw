---
title: "CDacl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDacl
- CDacl
- ATL.CDacl
dev_langs:
- C++
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
caps.latest.revision: 23
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: bb418919c26e3c0054a151b859cdf3f31c5d73a8
ms.lasthandoff: 02/24/2017

---
# <a name="cdacl-class"></a>CDacl 類別
這個類別是 DACL （判別存取控制清單） 結構的包裝函式。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CDacl : public CAcl
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDacl::CDacl](#cdacl)|建構函式。|  
|[CDacl:: ~ CDacl](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDacl::AddAllowedAce](#addallowedace)|將允許的 ACE （存取控制的項目） 加入至`CDacl`物件。|  
|[CDacl::AddDeniedAce](#adddeniedace)|新增拒絕的 ACE`CDacl`物件。|  
|[CDacl::GetAceCount](#getacecount)|在傳回的 Ace （存取控制的項目） 數目`CDacl`物件。|  
|[CDacl::RemoveAce](#removeace)|移除特定的 ACE （存取控制的項目）`CDacl`物件。|  
|[CDacl::RemoveAllAces](#removeallaces)|移除所有的 Ace 中包含`CDacl`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CDacl::operator =](#operator_eq)|指派運算子。|  
  
## <a name="remarks"></a>備註  
 物件的安全性描述元可以包含 DACL。 DACL 包含零或多個 Ace （存取控制的項目） 可識別使用者及群組可以存取的物件。 如果是空的 DACL （也就是包含零個 Ace），沒有明確授與存取，因此會隱含拒絕存取。 不過，如果物件的安全性描述元沒有 DACL，物件是未受保護，而且每個人都有完整存取權限。  
  
 若要擷取物件的 DACL，您必須是物件的擁有者，或具有 READ_CONTROL 物件的存取權。 若要變更物件的 DACL，您必須使用 WRITE_DAC 物件的存取權。  
  
 使用類別方法，可建立、 新增、 移除和刪除 Ace 從`CDacl`物件。 另請參閱[AtlGetDacl](http://msdn.microsoft.com/library/a0973648-0d46-4c1a-914f-bda861fe5d19)和[AtlSetDacl](http://msdn.microsoft.com/library/eb88ccb6-1f1b-444d-b0c9-8d5cd0dd6c0b)。  
  
 在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CDacl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h  
  
##  <a name="a-nameaddallowedacea--cdacladdallowedace"></a><a name="addallowedace"></a>CDacl::AddAllowedAce  
 將允許的 ACE （存取控制的項目） 加入至`CDacl`物件。  
  
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
 `rSid`  
 A [CSid](../../atl/reference/csid-class.md)物件。  
  
 `AccessMask`  
 指定允許的存取權限的遮罩指定`CSid`物件。  
  
 `AceFlags`  
 一組控制繼承 ACE 的位元旗標。  
  
 `pObjectType`  
 物件類型。  
  
 `pInheritedObjectType`  
 繼承的物件類型。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果 ACE 新增至`CDacl`物件， **false**失敗。  
  
### <a name="remarks"></a>備註  
 A`CDacl`物件包含零或多個 Ace （存取控制的項目） 可識別使用者及群組可以存取的物件。 這個方法會加入可讓您存取 ACE`CDacl`物件。  
  
> [!NOTE]
>  第二種`AddAllowedAce`只是在 Windows 2000 和更新版本。  
  
 請參閱[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)可以在中設定各種旗標的描述`AceFlags`參數。  
  
##  <a name="a-nameadddeniedacea--cdacladddeniedace"></a><a name="adddeniedace"></a>CDacl::AddDeniedAce  
 將拒絕的 ACE （存取控制的項目） 加入至`CDacl`物件。  
  
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
 `rSid`  
 `CSid` 物件。  
  
 `AccessMask`  
 指定要拒絕的存取權限的遮罩指定`CSid`物件。  
  
 `AceFlags`  
 一組控制繼承 ACE 的位元旗標。 預設為 0，在第一種形式的方法。  
  
 `pObjectType`  
 物件類型。  
  
 `pInheritedObjectType`  
 繼承的物件類型。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果 ACE 新增至`CDacl`物件， **false**失敗。  
  
### <a name="remarks"></a>備註  
 A`CDacl`物件包含零或多個 Ace （存取控制的項目） 可識別使用者及群組可以存取的物件。 這個方法會將拒絕存取的 ACE`CDacl`物件。  
  
> [!NOTE]
>  第二種`AddDeniedAce`只是在 Windows 2000 和更新版本。  
  
 請參閱[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)可以在中設定各種旗標的描述`AceFlags`參數。  
  
##  <a name="a-namecdacla--cdaclcdacl"></a><a name="cdacl"></a>CDacl::CDacl  
 建構函式。  
  
```
CDacl (const ACL& rhs) throw(...);  
CDacl () throw();
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 將現有**ACL** （存取控制清單） 的結構。  
  
### <a name="remarks"></a>備註  
 `CDacl`物件，可選擇性地建立使用現有**ACL**結構。 請務必注意，只有 DACL （判別存取控制清單），而且不 SACL （系統存取控制清單），會傳遞做為此參數。 偵錯組建中傳遞 SACL 會判斷提示。 在發行組建傳遞 SACL 會導致 Ace （存取控制的項目） 中的 ACL 會被忽略，而且不會發生錯誤。  
  
##  <a name="a-namedtora--cdaclcdacl"></a><a name="dtor"></a>CDacl:: ~ CDacl  
 解構函式。  
  
```
~CDacl () throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放取得物件，包括所有的 Ace （存取控制的項目） 所使用的任何資源[CDacl::RemoveAllAces](#removeallaces)。  
  
##  <a name="a-namegetacecounta--cdaclgetacecount"></a><a name="getacecount"></a>CDacl::GetAceCount  
 在傳回的 Ace （存取控制的項目） 數目`CDacl`物件。  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的 Ace 中包含數字`CDacl`物件。  
  
##  <a name="a-nameoperatoreqa--cdacloperator-"></a><a name="operator_eq"></a>CDacl::operator =  
 指派運算子。  
  
```
CDacl& operator= (const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 指派給現有的物件 ACL （存取控制清單）。  
  
### <a name="return-value"></a>傳回值  
 傳回參考更新的`CDacl`物件。  
  
### <a name="remarks"></a>備註  
 您應該確定您只將 DACL （判別存取控制清單） 傳遞給此函式。 傳遞 SACL （系統存取控制清單） 這個函式會導致偵錯組建中的判斷提示，但會導致發行組建中的任何錯誤。  
  
##  <a name="a-nameremoveacea--cdaclremoveace"></a><a name="removeace"></a>CDacl::RemoveAce  
 移除特定的 ACE （存取控制的項目）`CDacl`物件。  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 若要移除 ACE 的項目編製索引。  
  
### <a name="remarks"></a>備註  
 這個方法衍生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。  
  
##  <a name="a-nameremoveallacesa--cdaclremoveallaces"></a><a name="removeallaces"></a>CDacl::RemoveAllAces  
 移除所有的 Ace （存取控制的項目） 中包含`CDacl`物件。  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>備註  
 移除每個**ACE** （存取控制的項目） 結構 （如果有的話） 中`CDacl`物件。  
  
## <a name="see-also"></a>另請參閱  
 [安全性範例](../../visual-cpp-samples.md)   
 [CAcl 類別](../../atl/reference/cacl-class.md)   
 [Acl](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [Ace](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性的全域函式](../../atl/reference/security-global-functions.md)

