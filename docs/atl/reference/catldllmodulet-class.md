---
title: CAtlDllModuleT 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
ms.openlocfilehash: 7a5f8e7e489c8e0d573569ac7c4a8fb63f652732
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319007"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT 類別

此類表示 DLL 的模組。

## <a name="syntax"></a>語法

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
來自 的`CAtlDllModuleT`類 派生自 。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CatlDllModuleT:CatlDllModuleT](#catldllmodulet)|建構函式。|
|[CAtlDllModuleT:_CatlDllModuleT](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CatlDllmodulet::DllcanUnloadnow](#dllcanunloadnow)|測試是否可以卸載 DLL。|
|[CAtlDllmoduleT::DllgetclassObject](#dllgetclassobject)|返回類工廠。|
|[CAtlDllModuleT::DllMain](#dllmain)|動態連結庫 (DLL) 的可選入口點。|
|[CAtlDllModuleT::Dll註冊伺服器](#dllregisterserver)|將 DLL 中物件的條目添加到系統註冊表中。|
|[CAtlDllModuleT::Dllun寄存器伺服器](#dllunregisterserver)|刪除 DLL 中物件的系統註冊表中的項目。|
|[CAtlDllModuleT:取得類物件](#getclassobject)|返回類工廠。 [DllGetClassObject](#dllgetclassobject)呼叫 。|

## <a name="remarks"></a>備註

`CAtlDllModuleT`表示動態連結庫 (DLL) 的模組,並提供所有 DLL 專案使用的函數。 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)類的這種專業化包括對註冊的支援。

有關 ATL 中的模組的詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a>CatlDllModuleT:CatlDllModuleT

建構函式。

```
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a>CAtlDllModuleT:_CatlDllModuleT

解構函式。

```
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a>CatlDllmodulet::DllcanUnloadnow

測試是否可以卸載 DLL。

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>傳回值

如果 DLL 可以卸載,則返回S_OK,如果無法卸載,則返回S_FALSE。

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a>CAtlDllmoduleT::DllgetclassObject

返回類工廠。

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>參數

*rclsid*<br/>
要建立的物件的 CLSID。

*riid*<br/>
請求介面的 IID。

*Ppv*<br/>
指向*riid*標識的介面指標的指標。 如果物件不支援此介面,*則 ppv*設定為 NULL。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a>CAtlDllModuleT::DllMain

動態連結庫 (DLL) 的可選入口點。

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>參數

*dwReason*<br/>
如果設置為DLL_PROCESS_ATTACH,則禁用DLL_THREAD_ATTACH和DLL_THREAD_DETACH通知調用。

*lp保留*<br/>
已保留。

### <a name="return-value"></a>傳回值

始終返回 TRUE。

### <a name="remarks"></a>備註

禁用DLL_THREAD_ATTACH和DLL_THREAD_DETACH通知調用對於具有許多 DLL、經常創建和刪除線程且其 DLL 不需要這些線程級附件/分離通知的多線程應用程式可能是一種有用的優化。

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a>CAtlDllModuleT::Dll註冊伺服器

將 DLL 中物件的條目添加到系統註冊表中。

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
如果要註冊類型庫,則為 TRUE。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a>CAtlDllModuleT::Dllun寄存器伺服器

刪除 DLL 中物件的系統註冊表中的項目。

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>參數

*bUnRegTypeLib*<br/>
如果要從註冊表中刪除類型庫,則為 TRUE。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a>CAtlDllModuleT:取得類物件

建立指定的 CLSID 的物件。

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>參數

*rclsid*<br/>
要建立的物件的 CLSID。

*riid*<br/>
請求介面的 IID。

*Ppv*<br/>
指向*riid*標識的介面指標的指標。 如果物件不支援此介面,*則 ppv*設定為 NULL。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

此方法由[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)調用,並包含在向後相容性方面。

## <a name="see-also"></a>另請參閱

[CAtlModuleT 類別](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT 類別](../../atl/reference/catlexemodulet-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類](../../atl/atl-module-classes.md)
