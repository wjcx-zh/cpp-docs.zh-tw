---
title: 伺服器註冊全域功能
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: fb6353b52f487d0511c54223fe9e31dab88704b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325920"
---
# <a name="server-registration-global-functions"></a>伺服器註冊全域功能

這些函數支援在物件映射中註冊和取消註冊伺服器物件。

> [!IMPORTANT]
> 下表中列出的函數不能在 Windows 執行時中執行的應用程式中使用。

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|呼叫此函式可在物件對應中註冊每個物件。|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|呼叫此函式可在物件對應中移除每個物件的註冊。|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|呼叫此函式可註冊類別物件。|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|呼叫此功能是為了從 COM 模組撤消類物件。|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|調用此函數是為了獲取類物件。|

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="atlcommoduleregisterserver"></a><a name="atlcommoduleregisterserver"></a>AtlCom模組註冊伺服器

呼叫此函式可在物件對應中註冊每個物件。

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>參數

*pCom 模組*<br/>
指向 COM 模組的指標。

*bRegTypeLib*<br/>
如果要註冊類型庫,則為 TRUE。

*pCLSID*<br/>
指向要註冊的物件的 CLSID。 如果 NULL,則物件映射中的所有物件都將註冊。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

`AtlComModuleRegisterServer`走 ATL 自動生成的物件映射,並註冊地圖中的每個物件。 如果*pCLSID*不是 NULL,則僅註冊*pCLSID*引用的物件;否則,所有物件都已註冊。

此功能由[CAtlComModule 呼叫:註冊伺服器](catlcommodule-class.md#registerserver)。

## <a name="atlcommoduleunregisterserver"></a><a name="atlcommoduleunregisterserver"></a>AtlComModule 未註冊伺服器

呼叫此函式可在物件對應中移除每個物件的註冊。

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>參數

*pCom 模組*<br/>
指向 COM 模組的指標。

*bUnRegTypeLib*<br/>
如果要註冊類型庫,則為 TRUE。

*pCLSID*<br/>
指向要未註冊的物件的 CLSID。 如果 NULL 物件映射中的所有物件都將取消註冊。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

`AtlComModuleUnregisterServer`走 ATL 物件映射並取消註冊地圖中的每個物件。 如果*pCLSID*不是 NULL,則只有*pCLSID*引用的物件未註冊;否則,所有物件均未註冊。

此函數由[CAtlComModule 呼叫::取消註冊伺服器](catlcommodule-class.md#unregisterserver)。

## <a name="atlcommoduleregisterclassobjects"></a><a name="atlcommoduleregisterclassobjects"></a>AtlComModule 註冊類別

呼叫此函式可註冊類別物件。

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>參數

*pCom 模組*<br/>
指向 COM 模組的指標。

*dwCls 上下文*<br/>
指定要在其中運行類物件的上下文。 可能的值是CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER或CLSCTX_LOCAL_SERVER。 有關詳細資訊,請參閱[CLSCTX。](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx)

*dwFlags*<br/>
確定與類對象的連接類型。 可能的值是REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或REGCLS_MULTI_SEPARATE。 有關詳細資訊,請參閱[REGCLS。](/windows/win32/api/combaseapi/ne-combaseapi-regcls)

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CComModule::註冊類物件](ccommodule-class.md#registerclassobjects)(ATL 7.0中過時)和[CAtlExeModuleT::註冊類物件](catlexemodulet-class.md#registerclassobjects)使用此幫助程式函數。

## <a name="atlcommodulerevokeclassobjects"></a><a name="atlcommodulerevokeclassobjects"></a>AtlComModule 撤銷類別

呼叫此函式可從執行中的物件表格移除 Class Factory。

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>參數

*pCom 模組*<br/>
指向 COM 模組的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CComModule::撤銷類物件](ccommodule-class.md#revokeclassobjects)(ATL 7.0 中過時)和[CAtlExeModuleT::撤銷類物件](catlexemodulet-class.md#revokeclassobjects)使用此説明程式函數。

## <a name="atlcommodulegetclassobject"></a><a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject

呼叫此函式會傳回 Class Factory。

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>參數

*pCom 模組*<br/>
指向 COM 模組的指標。

*rclsid*<br/>
要建立的物件的 CLSID。

*riid*<br/>
請求介面的 IID。

*Ppv*<br/>
指向*riid*標識的介面指標的指標。 如果物件不支援此介面,*則 ppv*設定為 NULL。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CComModule:獲取類物件](ccommodule-class.md#getclassobject)(ATL 7.0中過時)和[CAtlDllModuleT::獲取類物件](catldllmodulet-class.md#getclassobject)使用此説明程式函數。

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
