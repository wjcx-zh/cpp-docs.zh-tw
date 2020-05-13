---
title: 安全全域功能
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
ms.openlocfilehash: 682d44aa80f5d6de521223dfd67db2813cb6738c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326026"
---
# <a name="security-global-functions"></a>安全全域功能

這些函數支援修改 SID 和 ACL 物件。

> [!IMPORTANT]
> 下表中列出的函數不能在 Windows 執行時中執行的應用程式中使用。

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

**標題:** atlsecurity.h

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a>AtlGetDacl

呼叫此函式可擷取所指定物件的判別存取控制清單 (DACL) 資訊。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>參數

*hObject*<br/>
處理要為其檢索安全資訊的物件。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚舉中的值,該枚舉指示*hObject*參數標識的物件類型。

*pDacl*<br/>
指向包含檢索的安全資訊的 DACL 物件的指標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

在除錯產生中,如果*hObject*或*pDacl*無效,將發生斷言錯誤。

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a>阿特爾塞特達克

呼叫此函式可設定所指定物件的判別存取控制清單 (DACL) 資訊。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
處理為其設置安全資訊的物件。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚舉中的值,該枚舉指示*hObject*參數標識的物件類型。

*rDacl*<br/>
包含新安全資訊的 DACL。

*dw繼承串流控制*<br/>
繼承流控件。 此值可以是 0(預設值)、PROTECTED_DACL_SECURITY_INFORMATION或UNPROTECTED_DACL_SECURITY_INFORMATION。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

在除錯產生中,如果*hObject*無效,或者*dwInheritFlowControl*不是三個允許的值之一,則會發生斷言錯誤。

### <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a>AtlGetGroupSid

呼叫此函式可擷取物件的群組安全性識別碼 (SID)。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
處理從中檢索安全資訊的物件。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚舉中的值,該枚舉指示*hObject*參數標識的物件類型。

*pSid*<br/>
指向將包含`CSid`新安全資訊的物件的指標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a>AtlSetGroupSid

呼叫此函式可設定物件的群組安全性識別碼 (SID)。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
處理為其設置安全資訊的物件。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚舉中的值,該枚舉指示*hObject*參數標識的物件類型。

*rSid*<br/>
包含`CSid`新安全資訊的物件。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a>AtlGetOwnerSid

呼叫此函式可擷取物件的擁有者安全性識別碼 (SID)。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
處理從中檢索安全資訊的物件。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚舉中的值,該枚舉指示*hObject*參數標識的物件類型。

*pSid*<br/>
指向將包含`CSid`新安全資訊的物件的指標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a>AtlSetOwnerSid

呼叫此函式可設定物件的擁有者安全性識別碼 (SID)。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
處理為其設置安全資訊的物件。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚舉中的值,該枚舉指示*hObject*參數標識的物件類型。

*rSid*<br/>
包含`CSid`新安全資訊的物件。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a>阿特爾茨薩克

呼叫此函式可擷取所指定物件的系統存取控制清單 (SACL) 資訊。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
處理從中檢索安全資訊的物件。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚舉中的值,該枚舉指示*hObject*參數標識的物件類型。

*pSacl*<br/>
指向 SACL 物件的指標,該物件將包含檢索到的安全資訊。

*b 要求需要的權限*<br/>
如果為 true,則函數將嘗試啟用SE_SECURITY_NAME許可權,並在完成後還原它。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

如果要`AtlGetSacl`在許多不同的物件上多次調用,則在調用函數之前啟用SE_SECURITY_NAME許可權將更為高效,將*bRequestDSs特權*設置為 false。

### <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a>阿特爾塞特薩克

呼叫此函式可設定所指定物件的系統存取控制清單 (SACL) 資訊。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
處理為其設置安全資訊的物件。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)枚舉中的值,該枚舉指示*hObject*參數標識的物件類型。

*rSacl*<br/>
包含新安全資訊的 SACL。

*dw繼承串流控制*<br/>
繼承流控件。 此值可以是 0(預設值)、PROTECTED_SACL_SECURITY_INFORMATION或UNPROTECTED_SACL_SECURITY_INFORMATION。

*b 要求需要的權限*<br/>
如果為 true,則函數將嘗試啟用SE_SECURITY_NAME許可權,並在完成後還原它。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

在除錯產生中,如果*hObject*無效,或者*dwInheritFlowControl*不是三個允許的值之一,則會發生斷言錯誤。

如果要`AtlSetSacl`在許多不同的物件上多次調用,則在調用函數之前啟用SE_SECURITY_NAME許可權將更為高效,將*bRequestDSs特權*設置為 false。

### <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a>AtlGet 安全性描述器

呼叫此函式可擷取所指物件的安全性描述元。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

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

*pszObject名稱*<br/>
指向 null 連接端接字串的指標,該字串指定從中檢索安全資訊的物件的名稱。

*ObjectType*<br/>
指定[SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type)的金舉中的值,該枚舉指示*pszObjectName*參數識別的物件類型。

*p 安全性描述器*<br/>
接收請求的安全描述符的物件。

*要求資訊*<br/>
一組[SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)位標誌,指示要檢索的安全資訊的類型。 此參數可以是以下值的組合。

*b 要求需要的權限*<br/>
如果為 true,則函數將嘗試啟用SE_SECURITY_NAME許可權,並在完成後還原它。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

如果要`AtlGetSecurityDescriptor`在許多不同的物件上多次調用,則在調用函數之前啟用SE_SECURITY_NAME許可權將更為高效,將*bRequestDSs特權*設置為 false。

### <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
