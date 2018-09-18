---
title: 伺服器註冊全域函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
dev_langs:
- C++
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fb3febbbaffc7c3a0de945fc9d30b544fd22188
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023302"
---
# <a name="server-registration-global-functions"></a>伺服器註冊全域函式

這些函式會提供註冊和取消註冊伺服器物件，物件對應中的支援。

> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|呼叫此函式可在物件對應中註冊每個物件。|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|呼叫此函式可在物件對應中移除每個物件的註冊。|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|呼叫此函式可註冊類別物件。|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|若要撤銷從 COM 模組類別物件，會呼叫此函數。|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|此函式會呼叫以取得類別物件。|  

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="atlcommoduleregisterserver"></a>  AtlComModuleRegisterServer

呼叫此函式可在物件對應中註冊每個物件。

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>參數

*pComModule*<br/>
COM 模組指標。

*bRegTypeLib*<br/>
如果型別程式庫是要註冊，則為 TRUE。

*Createtable*<br/>
要註冊之物件的 clsid 點。 如果是 NULL，將會登錄在物件對應中的所有物件。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

`AtlComModuleRegisterServer` ATL 自動產生物件對應並且在對應中註冊每個物件。 如果*Createtable*不是 NULL，則只有所參考的物件*Createtable*註冊; 否則會註冊的所有物件。

此函式會呼叫[CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver)。

##  <a name="atlcommoduleunregisterserver"></a>  AtlComModuleUnregisterServer

呼叫此函式可在物件對應中移除每個物件的註冊。

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>參數

*pComModule*<br/>
COM 模組指標。

*bUnRegTypeLib*<br/>
如果型別程式庫是要註冊，則為 TRUE。

*Createtable*<br/>
要移除註冊物件的 clsid 點。 如果 NULL 物件對應中的所有物件將都會取消註冊。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

`AtlComModuleUnregisterServer` 將逐步引導的 ATL 物件對應，並取消註冊在對應中的每個物件。 如果*Createtable*不是 NULL，則只有所參考的物件*Createtable*取消註冊; 否則會傳回所有物件都取消註冊。

此函式會呼叫[CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver)。

##  <a name="atlcommoduleregisterclassobjects"></a>  AtlComModuleRegisterClassObjects

呼叫此函式可註冊類別物件。

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>參數

*pComModule*<br/>
COM 模組指標。

*dwClsContext*<br/>
指定要執行的類別物件的內容。 可能的值為 CLSCTX_INPROC_SERVER、 CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。 請參閱[CLSCTX](https://msdn.microsoft.com/library/windows/desktop/ms693716)如需詳細資訊。

*dwFlags*<br/>
決定類別物件的連接類型。 可能的值為 REGCLS_SINGLEUSE、 REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。 請參閱[REGCLS](/windows/desktop/api/combaseapi/ne-combaseapi-tagregcls)如需詳細資訊。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

此協助程式函式會利用[CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) （已過時的 ATL 7.0） 和[CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects)。

##  <a name="atlcommodulerevokeclassobjects"></a>  AtlComModuleRevokeClassObjects

呼叫此函式可從執行中的物件表格移除 Class Factory。

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>參數

*pComModule*<br/>
COM 模組指標。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

此協助程式函式會利用[CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) （已過時的 ATL 7.0） 和[CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects)。

##  <a name="atlcommodulegetclassobject"></a>  AtlComModuleGetClassObject

呼叫此函式會傳回 Class Factory。

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>參數

*pComModule*<br/>
COM 模組指標。

*rclsid*<br/>
若要建立之物件的 CLSID。

*riid*<br/>
要求的介面 IID。

*ppv*<br/>
所識別之介面指標的指標*riid*。 如果物件不支援這個介面， *ppv*設為 NULL。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

此協助程式函式會利用[CComModule::GetClassObject](ccommodule-class.md#getclassobject) （已過時的 ATL 7.0） 和[CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject)。

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
