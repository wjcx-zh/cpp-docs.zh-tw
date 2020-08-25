---
title: 安全性全域函式
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
ms.openlocfilehash: 0b42fe10ef1de517677b35a9fe54d0c6a04ff748
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834488"
---
# <a name="security-global-functions"></a>安全性全域函式

這些函數支援修改 SID 和 ACL 物件。

> [!IMPORTANT]
> 下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|名稱|描述|
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

## <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a> AtlGetDacl

呼叫此函式可擷取所指定物件的判別存取控制清單 (DACL) 資訊。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>參數

*hObject*<br/>
物件的控制碼，以取得安全性資訊。

*ObjectType*<br/>
指定 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 列舉中的值，這個值會指出 *hObject* 參數所識別的物件類型。

*pDacl*<br/>
DACL 物件的指標，其中將包含已抓取的安全性資訊。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

在 debug 組建中，如果 *hObject* 或 *pDacl* 無效，就會發生判斷提示錯誤。

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a> AtlSetDacl

呼叫此函式可設定所指定物件的判別存取控制清單 (DACL) 資訊。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
要設定安全性資訊的物件控制碼。

*ObjectType*<br/>
指定 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 列舉中的值，這個值會指出 *hObject* 參數所識別的物件類型。

*rDacl*<br/>
包含新安全性資訊的 DACL。

*dwInheritanceFlowControl*<br/>
繼承流程式控制件。 這個值可以是 0 (預設) 、PROTECTED_DACL_SECURITY_INFORMATION 或 UNPROTECTED_DACL_SECURITY_INFORMATION。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

在 debug 組建中，如果 *hObject* 無效，或 *dwInheritanceFlowControl* 不是三個允許值的其中一個，就會發生判斷提示錯誤。

### <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a> AtlGetGroupSid

呼叫此函式可擷取物件的群組安全性識別碼 (SID)。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
要從其中取得安全性資訊的物件控制碼。

*ObjectType*<br/>
指定 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 列舉中的值，這個值會指出 *hObject* 參數所識別的物件類型。

*pSid*<br/>
物件的指標， `CSid` 該物件將包含新的安全性資訊。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a> AtlSetGroupSid

呼叫此函式可設定物件的群組安全性識別碼 (SID)。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
要設定安全性資訊的物件控制碼。

*ObjectType*<br/>
指定 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 列舉中的值，這個值會指出 *hObject* 參數所識別的物件類型。

*rSid*<br/>
`CSid`包含新安全性資訊的物件。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a> AtlGetOwnerSid

呼叫此函式可擷取物件的擁有者安全性識別碼 (SID)。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
要從其中取得安全性資訊的物件控制碼。

*ObjectType*<br/>
指定 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 列舉中的值，這個值會指出 *hObject* 參數所識別的物件類型。

*pSid*<br/>
物件的指標， `CSid` 該物件將包含新的安全性資訊。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a> AtlSetOwnerSid

呼叫此函式可設定物件的擁有者安全性識別碼 (SID)。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
要設定安全性資訊的物件控制碼。

*ObjectType*<br/>
指定 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 列舉中的值，這個值會指出 *hObject* 參數所識別的物件類型。

*rSid*<br/>
`CSid`包含新安全性資訊的物件。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a> AtlGetSacl

呼叫此函式可擷取所指定物件的系統存取控制清單 (SACL) 資訊。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>參數

*hObject*<br/>
要從其中取得安全性資訊的物件控制碼。

*ObjectType*<br/>
指定 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 列舉中的值，這個值會指出 *hObject* 參數所識別的物件類型。

*pSacl*<br/>
SACL 物件的指標，其中將包含已抓取的安全性資訊。

*bRequestNeededPrivileges*<br/>
若為 true，則函式會嘗試啟用 SE_SECURITY_NAME 許可權，並在完成時將它還原。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

如果 `AtlGetSacl` 在許多不同的物件上呼叫多次，則在呼叫函式之前啟用 SE_SECURITY_NAME 許可權一次，並將 *bRequestNeededPrivileges* 設定為 false，將會更有效率。

### <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a> AtlSetSacl

呼叫此函式可設定所指定物件的系統存取控制清單 (SACL) 資訊。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

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
要設定安全性資訊的物件控制碼。

*ObjectType*<br/>
指定 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 列舉中的值，這個值會指出 *hObject* 參數所識別的物件類型。

*rSacl*<br/>
包含新安全性資訊的 SACL。

*dwInheritanceFlowControl*<br/>
繼承流程式控制件。 這個值可以是 0 (預設) 、PROTECTED_SACL_SECURITY_INFORMATION 或 UNPROTECTED_SACL_SECURITY_INFORMATION。

*bRequestNeededPrivileges*<br/>
若為 true，則函式會嘗試啟用 SE_SECURITY_NAME 許可權，並在完成時將它還原。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

在 debug 組建中，如果 *hObject* 無效，或 *dwInheritanceFlowControl* 不是三個允許值的其中一個，就會發生判斷提示錯誤。

如果 `AtlSetSacl` 在許多不同的物件上呼叫多次，則在呼叫函式之前啟用 SE_SECURITY_NAME 許可權一次，並將 *bRequestNeededPrivileges* 設定為 false，將會更有效率。

### <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a> AtlGetSecurityDescriptor

呼叫此函式可擷取所指物件的安全性描述元。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

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

*pszObjectName*<br/>
指標，指向以 null 終止的字串，指定要從中取得安全性資訊的物件名稱。

*ObjectType*<br/>
指定 [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) 列舉中的值，這個值會指出 *pszObjectName* 參數所識別的物件類型。

*pSecurityDescriptor*<br/>
物件，這個物件會接收要求的安全描述項。

*requestedInfo*<br/>
一組 [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) 位旗標，表示要取出的安全性資訊類型。 這個參數可以是下列值的組合。

*bRequestNeededPrivileges*<br/>
若為 true，則函式會嘗試啟用 SE_SECURITY_NAME 許可權，並在完成時將它還原。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

如果 `AtlGetSecurityDescriptor` 在許多不同的物件上呼叫多次，則在呼叫函式之前啟用 SE_SECURITY_NAME 許可權一次，並將 *bRequestNeededPrivileges* 設定為 false，將會更有效率。

### <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)
