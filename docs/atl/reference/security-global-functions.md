---
title: "安全性全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: ff5afaaf2746d9e07eb9e06a079d34adb2f67109
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="security-global-functions"></a>安全性全域函式
這些函式提供修改 SID 和 ACL 物件的支援。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlGetDacl](#atlgetdacl)|呼叫此函式可擷取所指定物件的判別存取控制清單 (DACL) 資訊。|  
|[AtlSetDacl](#atlsetdacl)|呼叫此函式可設定所指定物件的判別存取控制清單 (DACL) 資訊。|  
|[AtlGetGroupSid](#atlgetgroupsid)|呼叫此函式可擷取物件的群組安全性識別碼 (SID)。|  
|[AtlSetGroupSid](#atlsetgroupsid)|呼叫此函式可設定物件的群組安全性識別碼 (SID)。|  
|[AtlGetOwnerSid](#atlgetownersid)|呼叫此函式可擷取物件的擁有者安全性識別碼 (SID)。|  
|[AtlSetOwnerSid](#atlsetownersid)|呼叫此函式可設定物件的擁有者安全性識別碼 (SID)。|  
|[AtlGetSacl](#atlgetsacl)|呼叫此函式可擷取所指定物件的系統存取控制清單 (SACL) 資訊。|  
|[AtlSetSacl](#atlsetsacl)|呼叫此函式可設定所指定物件的系統存取控制清單 (SACL) 資訊。|  
|[AtlGetSecurityDescriptor](#atlgetsecuritydescriptor)|呼叫此函式可擷取所指物件的安全性描述元。|  

## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h 

##  <a name="atlgetdacl"></a>AtlGetDacl  
 呼叫此函式可擷取所指定物件的判別存取控制清單 (DACL) 資訊。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 要擷取的安全性資訊物件的控制代碼。  
  
 `ObjectType`  
 指定的值從[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)列舉，指出物件所識別的型別`hObject`參數。  
  
 `pDacl`  
 將包含所擷取的安全性資訊的 DACL 物件指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，如果有任一個，會發生判斷提示錯誤`hObject`或`pDacl`無效。  
  
##  <a name="atlsetdacl"></a>AtlSetDacl  
 呼叫此函式可設定所指定物件的判別存取控制清單 (DACL) 資訊。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 要設定安全性資訊的物件的控制代碼。  
  
 `ObjectType`  
 指定的值從[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)列舉，指出物件所識別的型別`hObject`參數。  
  
 `rDacl`  
 包含新的安全性資訊的 DACL。  
  
 `dwInheritanceFlowControl`  
 繼承的流程控制。 這個值可以是 0 （預設）、 PROTECTED_DACL_SECURITY_INFORMATION 或 UNPROTECTED_DACL_SECURITY_INFORMATION。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`hObject`無效，或如果`dwInheritanceFlowControl`不是三個允許值之一。  
### <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h 

##  <a name="atlgetgroupsid"></a>AtlGetGroupSid  
 呼叫此函式可擷取物件的群組安全性識別碼 (SID)。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 要從中擷取安全性資訊的物件的控制代碼。  
  
 `ObjectType`  
 指定的值從[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)列舉，指出物件所識別的型別`hObject`參數。  
  
 `pSid`  
 指標`CSid`其中將包含新的安全性資訊的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  

### <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h 

##  <a name="atlsetgroupsid"></a>AtlSetGroupSid  
 呼叫此函式可設定物件的群組安全性識別碼 (SID)。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 要設定安全性資訊的物件的控制代碼。  
  
 `ObjectType`  
 指定的值從[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)列舉，指出物件所識別的型別`hObject`參數。  
  
 `rSid`  
 `CSid`物件，其中包含新的安全性資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  

### <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h 

##  <a name="atlgetownersid"></a>AtlGetOwnerSid  
 呼叫此函式可擷取物件的擁有者安全性識別碼 (SID)。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 要從中擷取安全性資訊的物件的控制代碼。  
  
 `ObjectType`  
 指定的值從[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)列舉，指出物件所識別的型別`hObject`參數。  
  
 `pSid`  
 指標`CSid`其中將包含新的安全性資訊的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  

### <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h 

##  <a name="atlsetownersid"></a>AtlSetOwnerSid  
 呼叫此函式可設定物件的擁有者安全性識別碼 (SID)。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 要設定安全性資訊的物件的控制代碼。  
  
 `ObjectType`  
 指定的值從[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)列舉，指出物件所識別的型別`hObject`參數。  
  
 `rSid`  
 `CSid`物件，其中包含新的安全性資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  

### <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h 

##  <a name="atlgetsacl"></a>AtlGetSacl  
 呼叫此函式可擷取所指定物件的系統存取控制清單 (SACL) 資訊。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 要從中擷取安全性資訊的物件的控制代碼。  
  
 `ObjectType`  
 指定的值從[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)列舉，指出物件所識別的型別`hObject`參數。  
  
 `pSacl`  
 SACL 物件將會包含所擷取的安全性資訊的指標。  
  
 `bRequestNeededPrivileges`  
 如果為 true，則函式會嘗試啟用 SE_SECURITY_NAME 權限，並將它還原完成。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 如果`AtlGetSacl`將許多不同的物件上呼叫多次會啟用 SE_SECURITY_NAME 權限後，才能呼叫函式，以更有效率`bRequestNeededPrivileges`設為 false。  

### <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h 

##  <a name="atlsetsacl"></a>AtlSetSacl  
 呼叫此函式可設定所指定物件的系統存取控制清單 (SACL) 資訊。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 要設定安全性資訊的物件的控制代碼。  
  
 `ObjectType`  
 指定的值從[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)列舉，指出物件所識別的型別`hObject`參數。  
  
 *rSacl*  
 SACL 包含新的安全性資訊。  
  
 `dwInheritanceFlowControl`  
 繼承的流程控制。 這個值可以是 0 （預設）、 PROTECTED_SACL_SECURITY_INFORMATION 或 UNPROTECTED_SACL_SECURITY_INFORMATION。  
  
 `bRequestNeededPrivileges`  
 如果為 true，則函式會嘗試啟用 SE_SECURITY_NAME 權限，並將它還原完成。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`hObject`無效，或如果`dwInheritanceFlowControl`不是三個允許值之一。  
  
 如果`AtlSetSacl`將許多不同的物件上呼叫多次會啟用 SE_SECURITY_NAME 權限後，才能呼叫函式，以更有效率`bRequestNeededPrivileges`設為 false。  

### <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h 

##  <a name="atlgetsecuritydescriptor"></a>AtlGetSecurityDescriptor  
 呼叫此函式可擷取所指物件的安全性描述元。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
 bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>參數  
 *pszObjectName*  
 以 null 終止的字串，指定要從中擷取安全性資訊的物件名稱的指標。  
  
 `ObjectType`  
 指定的值從[SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593)列舉，指出物件所識別的型別*pszObjectName*參數。  
  
 *pSecurityDescriptor*  
 物件，用於接收要求的安全性描述元。  
  
 *requestedInfo*  
 一組[SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573)位元旗標，表示要擷取的安全性資訊的類型。 這個參數可以是下列值的組合。  
  
 `bRequestNeededPrivileges`  
 如果為 true，則函式會嘗試啟用 SE_SECURITY_NAME 權限，並將它還原完成。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 true，失敗則傳回 false。  
  
### <a name="remarks"></a>備註  
 如果`AtlGetSecurityDescriptor`將許多不同的物件上呼叫多次會啟用 SE_SECURITY_NAME 權限後，才能呼叫函式，以更有效率`bRequestNeededPrivileges`設為 false。  

### <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h 
   
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)

