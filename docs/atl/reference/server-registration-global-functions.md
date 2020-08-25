---
title: 伺服器註冊全域函式
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: 4a84c311e34f1bc37b2f51e2152b6fcf2e46e2a3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835216"
---
# <a name="server-registration-global-functions"></a>伺服器註冊全域函式

這些函數提供在物件對應中註冊和取消註冊伺服器物件的支援。

> [!IMPORTANT]
> 下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|名稱|描述|
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|呼叫此函式可在物件對應中註冊每個物件。|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|呼叫此函式可在物件對應中移除每個物件的註冊。|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|呼叫此函式可註冊類別物件。|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|呼叫此函式可從 COM 模組撤銷類別物件。|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|呼叫此函式可取得類別物件。|

## <a name="requirements"></a>規格需求

**標頭：** atlbase.h。h

## <a name="atlcommoduleregisterserver"></a><a name="atlcommoduleregisterserver"></a> AtlComModuleRegisterServer

呼叫此函式可在物件對應中註冊每個物件。

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>參數

*pComModule*<br/>
COM 模組的指標。

*bRegTypeLib*<br/>
如果要註冊類型程式庫，則為 TRUE。

*pCLSID*<br/>
指向要註冊之物件的 CLSID。 如果是 Null，則會註冊物件對應中的所有物件。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

`AtlComModuleRegisterServer` 引導 ATL 自動產生的物件對應，並在地圖中註冊每個物件。 如果 *pCLSID* 不是 Null，則只會註冊 *pCLSID* 所參考的物件;否則，所有的物件都會註冊。

[CAtlComModule：： RegisterServer](catlcommodule-class.md#registerserver)會呼叫這個函式。

## <a name="atlcommoduleunregisterserver"></a><a name="atlcommoduleunregisterserver"></a> AtlComModuleUnregisterServer

呼叫此函式可在物件對應中移除每個物件的註冊。

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>參數

*pComModule*<br/>
COM 模組的指標。

*bUnRegTypeLib*<br/>
如果要註冊類型程式庫，則為 TRUE。

*pCLSID*<br/>
指向要取消註冊之物件的 CLSID。 如果為 Null，則會取消註冊物件對應中的所有物件。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

`AtlComModuleUnregisterServer` 引導 ATL 物件對應，並取消註冊對應中的每個物件。 如果 *pCLSID* 不是 Null，則只會取消註冊 *pCLSID* 所參考的物件;否則會取消註冊所有物件。

[CAtlComModule：： UnregisterServer](catlcommodule-class.md#unregisterserver)會呼叫這個函式。

## <a name="atlcommoduleregisterclassobjects"></a><a name="atlcommoduleregisterclassobjects"></a> AtlComModuleRegisterClassObjects

呼叫此函式可註冊類別物件。

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>參數

*pComModule*<br/>
COM 模組的指標。

*dwClsCoNtext*<br/>
指定要在其中執行類別物件的內容。 可能的值為 CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。 如需詳細資訊，請參閱 [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) 。

*dwFlags*<br/>
判斷類別物件的連線類型。 可能的值為 REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。 如需詳細資訊，請參閱 [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) 。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CComModule：： RegisterClassObjects](ccommodule-class.md#registerclassobjects) (在 ATL 7.0) 和[CAtlExeModuleT：： RegisterClassObjects](catlexemodulet-class.md#registerclassobjects)中淘汰的 helper 函式。

## <a name="atlcommodulerevokeclassobjects"></a><a name="atlcommodulerevokeclassobjects"></a> AtlComModuleRevokeClassObjects

呼叫此函式可從執行中的物件表格移除 Class Factory。

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>參數

*pComModule*<br/>
COM 模組的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CComModule：： RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (在 ATL 7.0) 和[CAtlExeModuleT：： RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects)中淘汰的 helper 函式。

## <a name="atlcommodulegetclassobject"></a><a name="atlcommodulegetclassobject"></a> AtlComModuleGetClassObject

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
COM 模組的指標。

*rclsid*<br/>
要建立之物件的 CLSID。

*riid*<br/>
所要求介面的 IID。

*Ppv*<br/>
由 *riid*識別之介面指標的指標。 如果物件不支援這個介面， *ppv* 會設為 Null。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CComModule：： GetClassObject](ccommodule-class.md#getclassobject) (在 ATL 7.0) 和[CAtlDllModuleT：： GetClassObject](catldllmodulet-class.md#getclassobject)中淘汰的 helper 函式。

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)
