---
title: "CPrivateObjectSecurityDesc 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
dev_langs:
- C++
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4845d652d2b1dceb8ffc0f2772f88565eb81e29
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc 類別
此類別代表私用物件安全性描述元物件。  
  
## <a name="syntax"></a>語法  
  
```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|建構函式。|  
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|呼叫此方法以將安全性描述元和其存取控制清單 (Acl) 轉換成其格式可支援自動傳播繼承的存取控制項目 (Ace)。|  
|[CPrivateObjectSecurityDesc::Create](#create)|呼叫這個方法來配置及初始化呼叫的資源管理員所建立的私用物件的自我關聯的安全性描述元。|  
|[CPrivateObjectSecurityDesc::Get](#get)|呼叫此方法以擷取私用物件的安全性描述元中的資訊。|  
|[CPrivateObjectSecurityDesc::Set](#set)|呼叫此方法以修改私用物件的安全性描述元。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator =](#operator_eq)|指派運算子。|  
  
## <a name="remarks"></a>備註  
 這個類別，衍生自[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)，提供方法來建立及管理 private 物件的安全性描述元。  
  
 如需在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)  
  
 `CPrivateObjectSecurityDesc`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsecurity.h  
  
##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit  
 呼叫此方法以將安全性描述元和其存取控制清單 (Acl) 轉換成其格式可支援自動傳播繼承的存取控制項目 (Ace)。  
  
```
bool ConvertToAutoInherit(  
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>參數  
 `pParent`  
 指標[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)參考物件的父容器物件。 如果沒有父容器，這個參數會是 NULL。  
  
 `ObjectType`  
 指標**GUID**識別與目前物件相關聯的物件類型的結構。 設定`ObjectType`為 NULL，如果物件沒有 GUID。  
  
 `bIsDirectoryObject`  
 指定新的物件是否可包含其他物件。 如果為 true 值表示新的物件是容器。 False 表示新的物件不是一個容器。  
  
 `GenericMapping`  
 指標[GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633)結構，指定從每個泛型的權限，為特定物件的權限的對應。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 這個方法會嘗試判斷是否的 Ace 判別存取控制清單 (DACL) 和目前的安全性描述元的系統存取控制清單 (SACL) 繼承自父安全性描述元。 它會呼叫[ConvertToAutoInheritPrivateObjectSecurity](http://msdn.microsoft.com/library/windows/desktop/aa376403)函式。  
  
##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc  
 建構函式。  
  
```
CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化 `CPrivateObjectSecurityDesc` 物件。  
  
##  <a name="dtor"></a>  CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc  
 解構函式。  
  
```
~CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放所有配置的資源，並刪除私用物件的安全性描述元。  
  
##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create  
 呼叫這個方法來配置及初始化呼叫的資源管理員所建立的私用物件的自我關聯的安全性描述元。  
  
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
 物件的建立者所提供的安全性描述元的指標。 如果物件的建立者不明確地將新物件的安全性資訊，請將這個參數設定為 NULL。  
  
 `bIsDirectoryObject`  
 指定新的物件是否可包含其他物件。 如果為 true 值表示新的物件是容器。 False 表示新的物件不是一個容器。  
  
 `Token`  
 若要參考[CAccessToken](../../atl/reference/caccesstoken-class.md)使建立物件的用戶端處理序的物件。  
  
 `GenericMapping`  
 指標[GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633)結構，指定從每個泛型的權限，為特定物件的權限的對應。  
  
 `ObjectType`  
 指標**GUID**識別與目前物件相關聯的物件類型的結構。 設定`ObjectType`為 NULL，如果物件沒有 GUID。  
  
 *bIsContainerObject*  
 指定新的物件是否可包含其他物件。 如果為 true 值表示新的物件是容器。 False 表示新的物件不是一個容器。  
  
 `AutoInheritFlags`  
 一組位元旗標，以控制存取控制項目 (Ace) 繼承自`pParent`。 請參閱[CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581)如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[CreatePrivateObjectSercurity](http://msdn.microsoft.com/library/windows/desktop/aa376405)或[CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581)。  
  
 第二種方法可讓指定的新物件的物件類型的 GUID 或控制如何繼承 Ace。  
  
> [!NOTE]
>  自我關聯的安全性描述元是記憶體的連續區塊中儲存所有的安全性資訊的安全性描述元。  
  
##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get  
 呼叫此方法以擷取私用物件的安全性描述元中的資訊。  
  
```
bool Get(  
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```  
  
### <a name="parameters"></a>參數  
 `si`  
 一組的位元旗標，表示要擷取的安全性描述元組件。 這個值可以是多種[SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573)位元旗標。  
  
 `pResult`  
 指標[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)接收要求資訊的複本，從指定的安全性描述元物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 安全性描述元是結構和相關聯的資料，其中包含安全性實體物件的安全性資訊。  
  
##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =  
 指派運算子。  
  
```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rhs`  
 `CPrivateObjectSecurityDesc`將指派給目前物件的物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CPrivateObjectSecurityDesc`物件。  
  
##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set  
 呼叫此方法以修改私用物件的安全性描述元。  
  
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
 一組的位元旗標，表示要設定安全性描述元組件。 這個值可以是多種[SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573)位元旗標。  
  
 *修改*  
 指標[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件。 此安全性描述元的組件由`si`參數會套用至物件的安全性描述元。  
  
 `GenericMapping`  
 指標[GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633)結構，指定從每個泛型的權限，為特定物件的權限的對應。  
  
 `Token`  
 若要參考[CAccessToken](../../atl/reference/caccesstoken-class.md)使建立物件的用戶端處理序的物件。  
  
 `AutoInheritFlags`  
 一組位元旗標，以控制存取控制項目 (Ace) 繼承自`pParent`。 請參閱[CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581)如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 第二種方法允許指定物件的物件類型的 GUID 或控制如何繼承 Ace。  
  
## <a name="see-also"></a>請參閱  
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性全域函式](../../atl/reference/security-global-functions.md)   
 [CSecurityDesc 類別](../../atl/reference/csecuritydesc-class.md)
