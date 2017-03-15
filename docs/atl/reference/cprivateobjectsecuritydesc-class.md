---
title: "CPrivateObjectSecurityDesc 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CPrivateObjectSecurityDesc
- ATL::CPrivateObjectSecurityDesc
- CPrivateObjectSecurityDesc
dev_langs:
- C++
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
caps.latest.revision: 20
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 154a4229f8963d3081e6e0518354d17968ee0e20
ms.lasthandoff: 02/24/2017

---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc 類別
此類別代表私用物件安全性描述元物件。  
  
## <a name="syntax"></a>語法  
  
```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|建構函式。|  
|[CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|呼叫這個方法，將安全性描述元和其存取控制清單 (Acl) 轉換成可支援自動傳用可繼承的存取控制項目 (Ace) 的格式。|  
|[CPrivateObjectSecurityDesc::Create](#create)|呼叫這個方法來配置及初始化呼叫資源管理員所建立的私用物件的自我關聯的安全性描述元。|  
|[CPrivateObjectSecurityDesc::Get](#get)|呼叫這個方法來擷取私人物件安全性描述元中的資訊。|  
|[CPrivateObjectSecurityDesc::Set](#set)|呼叫這個方法來修改私用物件的安全性描述元。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 =](#operator_eq)|指派運算子。|  
  
## <a name="remarks"></a>備註  
 這個類別衍生自[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)，提供方法來建立和管理私用物件的安全性描述元。  
  
 在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)  
  
 `CPrivateObjectSecurityDesc`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h  
  
##  <a name="a-nameconverttoautoinherita--cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a>CPrivateObjectSecurityDesc::ConvertToAutoInherit  
 呼叫這個方法，將安全性描述元和其存取控制清單 (Acl) 轉換成可支援自動傳用可繼承的存取控制項目 (Ace) 的格式。  
  
```
bool ConvertToAutoInherit(  
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>參數  
 `pParent`  
 指標[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)參考物件的父容器物件。 如果沒有父容器，這個參數是 NULL。  
  
 `ObjectType`  
 指標**GUID**識別與目前物件相關聯的物件類型的結構。 設定`ObjectType`為 NULL，如果物件沒有 GUID。  
  
 `bIsDirectoryObject`  
 指定新的物件是否可以包含其他物件。 如果為 true 值表示新的物件是一個容器。 False 表示新的物件不是一個容器。  
  
 `GenericMapping`  
 指標[GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633)結構，指定從每個泛型的權限，為特定物件的權限的對應。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 這個方法會嘗試判斷是否 Ace 判別存取控制清單 (DACL) 和目前的安全性描述元的系統存取控制清單 (SACL) 被繼承自父安全性描述元中。 它會呼叫[ConvertToAutoInheritPrivateObjectSecurity](http://msdn.microsoft.com/library/windows/desktop/aa376403)函式。  
  
##  <a name="a-namecprivateobjectsecuritydesca--cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc  
 建構函式。  
  
```
CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化`CPrivateObjectSecurityDesc`物件。  
  
##  <a name="a-namedtora--cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a>CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc  
 解構函式。  
  
```
~CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放所有配置的資源，並刪除私用物件的安全性描述元。  
  
##  <a name="a-namecreatea--cprivateobjectsecuritydesccreate"></a><a name="create"></a>CPrivateObjectSecurityDesc::Create  
 呼叫這個方法來配置及初始化呼叫資源管理員所建立的私用物件的自我關聯的安全性描述元。  
  
```
bool Create(  
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(  
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>參數  
 `pParent`  
 指標[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)參考在其中建立新物件的父目錄物件。 如果沒有父目錄，請設為 NULL。  
  
 `pCreator`  
 物件的建立者所提供的安全性描述元的指標。 如果物件的建立者明確傳遞新物件的安全性資訊，請將這個參數設定為 NULL。  
  
 `bIsDirectoryObject`  
 指定新的物件是否可以包含其他物件。 如果為 true 值表示新的物件是一個容器。 False 表示新的物件不是一個容器。  
  
 `Token`  
 若要參考[CAccessToken](../../atl/reference/caccesstoken-class.md)用戶端處理序，因而建立物件的物件。  
  
 `GenericMapping`  
 指標[GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633)結構，指定從每個泛型的權限，為特定物件的權限的對應。  
  
 `ObjectType`  
 指標**GUID**識別與目前物件相關聯的物件類型的結構。 設定`ObjectType`為 NULL，如果物件沒有 GUID。  
  
 *bIsContainerObject*  
 指定新的物件是否可以包含其他物件。 如果為 true 值表示新的物件是一個容器。 False 表示新的物件不是一個容器。  
  
 `AutoInheritFlags`  
 一組位元旗標，以控制存取控制項目 (Ace) 都繼承自`pParent`。 請參閱[CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581)如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[CreatePrivateObjectSercurity](http://msdn.microsoft.com/library/windows/desktop/aa376405)或[CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581)。  
  
 第二個方法，可允許指定的新物件的物件類型的 GUID 或控制如何繼承 Ace，才可在執行 Windows 2000 系統上及更新版本。  
  
> [!NOTE]
>  自我關聯的安全性描述元是記憶體的連續區塊中會儲存所有的安全性資訊的安全性描述元。  
  
##  <a name="a-namegeta--cprivateobjectsecuritydescget"></a><a name="get"></a>CPrivateObjectSecurityDesc::Get  
 呼叫這個方法來擷取私人物件安全性描述元中的資訊。  
  
```
bool Get(  
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```  
  
### <a name="parameters"></a>參數  
 `si`  
 一組的位元旗標，表示要擷取的安全性描述元的組件。 這個值可以是結合[SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573)位元旗標。  
  
 `pResult`  
 指標[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)接收要求資訊的複本，從指定的安全性描述元的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 安全性描述元是結構和相關聯的資料，其中包含安全性實體物件的安全性資訊。  
  
##  <a name="a-nameoperatoreqa--cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a>CPrivateObjectSecurityDesc::operator =  
 指派運算子。  
  
```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 `CPrivateObjectSecurityDesc`物件指派給目前的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回更新`CPrivateObjectSecurityDesc`物件。  
  
##  <a name="a-nameseta--cprivateobjectsecuritydescset"></a><a name="set"></a>CPrivateObjectSecurityDesc::Set  
 呼叫這個方法來修改私用物件的安全性描述元。  
  
```
bool Set(  
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(  
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```  
  
### <a name="parameters"></a>參數  
 `si`  
 一組位元旗標，指出若要設定的安全性描述元的組件。 這個值可以是結合[SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573)位元旗標。  
  
 *修改*  
 指標[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件。 這個安全性描述元的組件以`si`參數會套用至物件的安全性描述元。  
  
 `GenericMapping`  
 指標[GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633)結構，指定從每個泛型的權限，為特定物件的權限的對應。  
  
 `Token`  
 若要參考[CAccessToken](../../atl/reference/caccesstoken-class.md)用戶端處理序，因而建立物件的物件。  
  
 `AutoInheritFlags`  
 一組位元旗標，以控制存取控制項目 (Ace) 都繼承自`pParent`。 請參閱[CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581)如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 第二個方法，可允許指定之物件的物件類型的 GUID 或控制如何繼承 Ace，才可在執行 Windows 2000 系統上及更新版本。  
  
## <a name="see-also"></a>另請參閱  
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性的全域函式](../../atl/reference/security-global-functions.md)   
 [CSecurityDesc 類別](../../atl/reference/csecuritydesc-class.md)

