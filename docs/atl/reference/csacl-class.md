---
title: CSacl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 817875dd32457fa47eafca9d634bc2e7cc8e079d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206566"
---
# <a name="csacl-class"></a>CSacl 類別
這個類別是 SACL （系統存取控制清單） 結構的包裝函式。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CSacl : public CAcl
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSacl::CSacl](#csacl)|建構函式。|  
|[CSacl::~CSacl](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSacl::AddAuditAce](#addauditace)|將稽核的存取控制項目 (ACE) 加入至`CSacl`物件。|  
|[CSacl::GetAceCount](#getacecount)|在傳回的存取控制項目 (Ace) 數目`CSacl`物件。|  
|[CSacl::RemoveAce](#removeace)|移除特定的 ACE （存取控制項目）`CSacl`物件。|  
|[CSacl::RemoveAllAces](#removeallaces)|移除所有的 Ace 中包含`CSacl`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CSacl::operator =](#operator_eq)|指派運算子。|  
  
## <a name="remarks"></a>備註  
 SACL 包含指定的網域控制站的安全性事件記錄檔中產生稽核記錄的存取嘗試類型的存取控制項目 (Ace)。 請注意，SACL 會產生記錄項目只在嘗試存取的發生位置的網域控制站上，而不是在每個網域控制站，其中包含物件的複本。  
  
 若要設定或擷取物件的安全性描述元中 SACL，SE_SECURITY_NAME 權限必須能夠存取權杖的要求的執行緒中。 系統管理員群組已經依預設，授與此權限，它可以授與其他使用者或群組。 具有權限授與並不是全部所需： 在執行權限所定義的作業之前，將權限必須啟用安全性的存取權杖中才能生效。 模型可讓您只能針對特定的系統作業，啟用與則停用時不再需要的權限。 請參閱[AtlGetSacl](security-global-functions.md#atlgetsacl)並[AtlSetSacl](security-global-functions.md#atlsetsacl)啟用 SE_SECURITY_NAME 的範例。  
  
 使用提供給加入、 移除、 建立和刪除從 Ace 類別方法`SACL`物件。 另請參閱[AtlGetSacl](security-global-functions.md#atlgetsacl)並[AtlSetSacl](security-global-functions.md#atlsetsacl)。  
  
 在 Windows 中的存取控制模型的簡介，請參閱 <<c0> [ 存取控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAcl](../../atl/reference/cacl-class.md)  
  
 `CSacl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsecurity.h  
  
##  <a name="addauditace"></a>  CSacl::AddAuditAce  
 將稽核的存取控制項目 (ACE) 加入至`CSacl`物件。  
  
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
 *rSid*  
 [CSid](../../atl/reference/csid-class.md)物件。  
  
 *AccessMask*  
 指定要稽核的存取權限遮罩指定`CSid`物件。  
  
 *bSuccess*  
 指定是否要稽核允許的存取嘗試。 設定此旗標，true 以啟用稽核;否則，請將它設定為 false。  
  
 *bFailure*  
 指定是否要稽核拒絕的存取嘗試。 設定此旗標，true 以啟用稽核;否則，請將它設定為 false。  
  
 *AceFlags*  
 一組控制 ACE 繼承的位元旗標。  
  
 *pObjectType*  
 物件類型。  
  
 *pInheritedObjectType*  
 繼承的物件型別。  
  
### <a name="return-value"></a>傳回值  
 會傳回 TRUE，如果 ACE 新增至`CSacl`物件，FALSE 失敗。  
  
### <a name="remarks"></a>備註  
 A`CSacl`物件包含指定的安全性事件記錄檔中產生稽核記錄的存取嘗試類型的存取控制項目 (Ace)。 此方法會將這類 ACE 以`CSacl`物件。  
  
 請參閱[ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header)如需可以在中設定各種旗標的說明*AceFlags*參數。  
  
##  <a name="csacl"></a>  CSacl::CSacl  
 建構函式。  
  
```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 *rhs*  
 將現有`ACL`（存取控制清單） 結構。  
  
### <a name="remarks"></a>備註  
 `CSacl`物件可以選擇性地建立使用現有`ACL`結構。 請確定這個參數是系統存取控制清單 (SACL) 和非判別存取控制清單 (DACL)。 在偵錯組建中，如果未提供 DACL，則會發生判斷提示。 在發行組建中 DACL 的任何項目都會被忽略。  
  
##  <a name="dtor"></a>  CSacl::~CSacl  
 解構函式。  
  
```
~CSacl() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放取得的物件，包括所有存取控制項目 (Ace) 的任何資源。  
  
##  <a name="getacecount"></a>  CSacl::GetAceCount  
 在傳回的存取控制項目 (Ace) 數目`CSacl`物件。  
  
```
UINT GetAceCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回中所包含的 Ace 數目`CSacl`物件。  
  
##  <a name="operator_eq"></a>  CSacl::operator =  
 指派運算子。  
  
```
CSacl& operator=(const ACL& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 *rhs*  
 `ACL` （存取控制清單） 指派給現有的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新的參考`CSacl`物件。 請確認`ACL`參數是實際系統存取控制清單 (SACL) 而非判別存取控制清單 (DACL)。 在判斷提示，就會發生的偵錯組建和發行組建中`ACL`參數將會被忽略。  
  
##  <a name="removeace"></a>  CSacl::RemoveAce  
 移除特定的 ACE （存取控制項目）`CSacl`物件。  
  
```
void RemoveAce(UINT nIndex) throw();
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 若要移除的 ACE 項目索引。  
  
### <a name="remarks"></a>備註  
 這個方法衍生自[CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat)。  
  
##  <a name="removeallaces"></a>  CSacl::RemoveAllAces  
 移除所有存取控制項目 (Ace) 中包含`CSacl`物件。  
  
```
void RemoveAllAces() throw();
```  
  
### <a name="remarks"></a>備註  
 移除每個`ACE`結構 （如果有的話）`CSacl`物件。  
  
## <a name="see-also"></a>另請參閱  
 [CAcl 類別](../../atl/reference/cacl-class.md)   
 [Acl](/windows/desktop/SecAuthZ/access-control-lists)   
 [Ace](/windows/desktop/SecAuthZ/access-control-entries)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性全域函式](../../atl/reference/security-global-functions.md)
