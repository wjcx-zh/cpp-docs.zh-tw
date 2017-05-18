---
title: "CSacl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
dev_langs:
- C++
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
caps.latest.revision: 22
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: bd9ef9932938cfe5ec65965b3a40116da7f43b90
ms.contentlocale: zh-tw
ms.lasthandoff: 03/31/2017

---
# <a name="csacl-class"></a>CSacl 類別
這個類別是 SACL （系統存取控制清單） 結構的包裝函式。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CSacl : public CAcl
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSacl::CSacl](#csacl)|建構函式。|  
|[CSacl:: ~ CSacl](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSacl::AddAuditAce](#addauditace)|將稽核存取控制項目 (ACE) 加入至`CSacl`物件。|  
|[CSacl::GetAceCount](#getacecount)|傳回中的存取控制項目 (Ace) 數目`CSacl`物件。|  
|[CSacl::RemoveAce](#removeace)|移除特定的 ACE （存取控制的項目） **CSacl**物件。|  
|[CSacl::RemoveAllAces](#removeallaces)|移除所有的 Ace 中包含`CSacl`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CSacl::operator =](#operator_eq)|指派運算子。|  
  
## <a name="remarks"></a>備註  
 SACL 包含指定的網域控制站的安全性事件記錄檔中產生稽核記錄的存取嘗試類型的存取控制項目 (Ace)。 請注意，SACL 會產生記錄項目只嘗試存取發生所在的網域控制站，而非每個網域控制站，其中包含物件的複本。  
  
 若要設定或擷取物件的安全性描述元中 SACL，必須啟用 SE_SECURITY_NAME 權限要求之執行緒的存取權杖中。 系統管理員群組已經依預設，授與此權限，它可以授與給其他使用者或群組。 需要權限授與便不需要的所有︰ 在執行特殊權限所定義的作業之前，權限必須在啟用安全性的存取權杖才能生效。 此模型可讓權限可以為僅適用於特定的系統作業，然後在不再需要時停用。 請參閱[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl](security-global-functions.md#atlsetsacl)啟用 SE_SECURITY_NAME 的範例。  
  
 使用要加入、 移除、 建立和刪除 Ace 從提供的類別方法**SACL**物件。 另請參閱[AtlGetSacl](security-global-functions.md#atlgetsacl)和[AtlSetSacl](security-global-functions.md#atlsetsacl)。  
  
 如需在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h  
  
##  <a name="addauditace"></a>CSacl::AddAuditAce  
 將稽核存取控制項目 (ACE) 加入至`CSacl`物件。  
  
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
 `rSid`  
 [CSid](../../atl/reference/csid-class.md)物件。  
  
 `AccessMask`  
 指定要稽核的存取權限的遮罩指定`CSid`物件。  
  
 `bSuccess`  
 指定是否要稽核會允許的存取嘗試次數。 設定此旗標，true 會啟用稽核。否則，將它設定為 false。  
  
 *bFailure*  
 指定是否要稽核會拒絕的存取嘗試次數。 設定此旗標，true 會啟用稽核。否則，將它設定為 false。  
  
 `AceFlags`  
 一組控制 ACE 繼承的位元旗標。  
  
 `pObjectType`  
 物件類型。  
  
 `pInheritedObjectType`  
 繼承的物件類型。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果 ACE 新增至`CSacl`物件**false**失敗。  
  
### <a name="remarks"></a>備註  
 A`CSacl`物件包含指定的安全性事件記錄檔中產生稽核記錄的存取嘗試類型的存取控制項目 (Ace)。 這個方法會加入至這類 ACE`CSacl`物件。 第二種`AddAuditAce`才可於 Windows 2000 和更新版本。  
  
 請參閱[ACE_HEADER](http://msdn.microsoft.com/library/windows/desktop/aa374919)可以在中設定各種旗標的描述`AceFlags`參數。  
  
##  <a name="csacl"></a>CSacl::CSacl  
 建構函式。  
  
```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 現有**ACL** （存取控制清單） 結構。  
  
### <a name="remarks"></a>備註  
 `CSacl`物件可以選擇性地建立使用現有**ACL**結構。 確定此參數是系統存取控制清單 (SACL) 並不是判別存取控制清單 (DACL)。 在偵錯組建中，如果未提供 DACL，則會發生判斷提示。 在發行組建會忽略來自 DACL 的任何項目。  
  
##  <a name="dtor"></a>CSacl:: ~ CSacl  
 解構函式。  
  
```
~CSacl() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放物件，包括所有存取控制項目 (Ace) 來取得所有資源。  
  
##  <a name="getacecount"></a>CSacl::GetAceCount  
 傳回中的存取控制項目 (Ace) 數目`CSacl`物件。  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回中所包含的 Ace 數目`CSacl`物件。  
  
##  <a name="operator_eq"></a>CSacl::operator =  
 指派運算子。  
  
```
CSacl& operator=(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 **ACL** （存取控制清單），將指派給現有的物件。  
  
### <a name="return-value"></a>傳回值  
 將參考傳回給更新`CSacl`物件。 請確認**ACL**參數是實際系統存取控制清單 (SACL) 而不是判別存取控制清單 (DACL)。 在偵錯組建，就會進行判斷提示，並在發行組建中**ACL**參數將會被忽略。  
  
##  <a name="removeace"></a>CSacl::RemoveAce  
 移除特定的 ACE （存取控制的項目） **CSacl**物件。  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 若要移除 ACE 項目索引。  
  
### <a name="remarks"></a>備註  
 這個方法衍生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。  
  
##  <a name="removeallaces"></a>CSacl::RemoveAllAces  
 移除存取控制項目 (Ace) 中所包含的所有`CSacl`物件。  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>備註  
 移除每個**ACE**結構 （如果有的話）`CSacl`物件。  
  
## <a name="see-also"></a>另請參閱  
 [CAcl 類別](../../atl/reference/cacl-class.md)   
 [Acl](http://msdn.microsoft.com/library/windows/desktop/aa374872)   
 [Ace](http://msdn.microsoft.com/library/windows/desktop/aa374868)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性全域函式](../../atl/reference/security-global-functions.md)

